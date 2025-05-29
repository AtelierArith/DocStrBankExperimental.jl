### BritishNationalGrid

Convert between longitude and latitude and coordinates of the British National Grid.

The `BNGPoint` type and constructor is used to create points with easting and northings  These are given relative to the grid's false origin southwest of the Isles of Scilly.

Exported functions:

  * `BNGPoint`: Construct a new point on the grid
  * `gridref`: Return a string with an n-figure grid reference
  * `lonlat`: Convert a grid point to WGS84 longitude and latitude
  * `square`: Determine which National Grid 100 km square a point is in

The following functions are also exported.  Note that these do not check that the longitude and latitude, or easting and northing, supplied to these functions are within the valid region of the grid, and so **these functions should be used with care**.

  * `bng2lonlat`: Return (unchecked) longitude and latitude from BNG coordinates
  * `lonlat2bng`: Return (unchecked) BNG coordinates from a longitude and latitude

See the documentation for each function to learn more.
