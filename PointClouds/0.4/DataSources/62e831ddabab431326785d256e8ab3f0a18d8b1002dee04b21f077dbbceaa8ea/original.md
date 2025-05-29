```
gettiles([src::DataSource]; lat, lon, crs = "EPSG:4326", limit = 100)
```

Query the available data sources or a specific source `src` for tiles of point-cloud data. This returns an array of `PointCloudTile`s, which only contain the database entries. These value can be passed to the `LAS` constructor to download and load the point data itself. They can also be passed to `minimum`/`maximum`/`extent` to get the coordinate range covered by each tile.

The `lon` (or equivalently `x`) and `lat` (or `y`) keyword arguments specify the latitude and longitude values for the spatial query, specified in the [WGS 84](https://en.wikipedia.org/wiki/World_Geodetic_System) coordinate reference system (CRS), which is also used by GPS and many online maps. The query will search for tiles at a point, within a box, or within a polygon, depending on whether one, two, or multiple coordinate values are provided. Coordinates can also be specified in a different CRS by supplying the `crs` argument.

The `limit` argument specifies the maximum number of tiles that are requested from each data source. The APIs that are queried may have their own limits that cannot be exceeded (1000 for ScienceBase). Beyond those paging is required (i.e. requesting more results with an offset), which is not currently supported by `gettiles`.
