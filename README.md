# UFO Challenge

## Overview of Project

After helping Dana build a webpage with a dynamic table containing UFO data, she wanted to expand the search functionality to more categories. We used the following languages to create/modify the webpage and import the data contained in the javascript file:

- HTML
- Javascript
- CSS

Because we had to account for multiple search criteria, we took the following steps to modify our app.js:

1. Created an object to store any entered search terms

```
// 1. Create a variable to keep track of all the filters as an object.
let filters = {};
```

2. Build a function to loop through the filters object and rebuild the table:

```
// 7. Use this function to filter the table when data is entered.
function filterTable() {
  

  // 8. Set the filtered data to the tableData.
  let filteredData = tableData;

  // 9. Loop through all of the filters and keep any data that
  // matches the filter values
  Object.entries(filters).forEach(([key, val]) => {
    filteredData = filteredData.filter(row=> row[key] === val);
  });

  // 10. Finally, rebuild the table using the filtered data
  buildTable(filteredData);
}
```
3. Replaced our d3 event with the following in order to capture any changes since we got rid of the 'filter' button:

```
// 2. Attach an event to listen for changes to each filter
d3.selectAll("input").on("change", updateFilters);
```

## Results

This webpage would be perfect for planning a UFO sighting adventure. Our filters allow for a user to plan an itinerary by filtering States, Cities, etc.

Here's how our complete set looks:

![full_table](https://github.com/rivas-j/UFOs/blob/386b2c792fa1d5e239ac6fe8acdb66db9ac1604b/images/updated_table.png)

If we want to help an UFO enthusiast plan a quick trip to any fireball sightings in California, we can first filter by state ('ca'):

![california_filter](https://github.com/rivas-j/UFOs/blob/386b2c792fa1d5e239ac6fe8acdb66db9ac1604b/images/california_filter.png)

We can then filter by shape ('fireball'):

![california_fireball_filter](https://github.com/rivas-j/UFOs/blob/386b2c792fa1d5e239ac6fe8acdb66db9ac1604b/images/california-fireballs_filter.png)

Presto! We have a roadtrip!

## Summary: In a summary statement, describe one drawback of this new design and two recommendations for further development.

This webpage presents a very useful way to navigate the extensive dataset of UFO sightings over the years. One big drawback to the changes we've made is the absesnse of any buttons on the page. Here are some slight tweaks we're suggesting to improve user experience:

- Add a 'Clear Search' button in the index.html file below our filter table, with accompanying javascript that will clear our filters on the event of a button click. This will allow an easy way for the end user to perform multiple queries without having to reload the page
- Allow the user to sort the table by each column. We can accomplish this by adding a sort form under the filter form on the left hand side with input boxes asking for the column and whether they want ascending or descending order
