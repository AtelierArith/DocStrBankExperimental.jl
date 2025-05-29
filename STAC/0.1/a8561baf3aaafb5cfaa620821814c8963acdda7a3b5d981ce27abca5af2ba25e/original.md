```
search(cat::Catalog, collections, lon_range, lat_range, datetime;
       limit = 200,
       filter = nothing,
       query = nothing,
)
```

Search items in a `STAC.Catalog` `cat` belong to the `collections` within the longitude range `lon_range` (start and end longitude), latitude range `lat_range`, and time range (start and end `DateTime`).

The optional `filter` parameter allows to filter the resuts using [CQL2](https://github.com/stac-api-extensions/filter) (see example below). [STACQL](https://github.com/stac-api-extensions/query/blob/3c42ab316dbba0089803e77fb572dc0cfc4ee4fe/README.md) is also supported via the optional `query` parameter. It is recommended to use CQL2 instead of STACQL. This `filter` and `query` are experimental and currently only part of the STAC as a "candiate" or "pilot".

The function `search` returns an julia `Channel` with the search results over which one can only iterate once. If the results should be saved use `search_results = collect(search(cat,...))`.

Example:

```julia
using STAC, Dates
collections = ["landsat-8-c2-l2"]
time_range = (DateTime(2018,01,01), DateTime(2018,01,02))
lon_range = (2.51357303225, 6.15665815596)
lat_range = (49.5294835476, 51.4750237087)

catalog = STAC.Catalog("https://planetarycomputer.microsoft.com/api/stac/v1")

search_results = collect(search(catalog, collections, lon_range, lat_range, time_range))
```

Example with additional CQL2 filter

```julia
filter = Dict(
   "op" => "<=",
   "args" => [Dict("property" => "eo:cloud_cover"), 61]
)

search_results = collect(
        search(cat, collections,
               lon_range, lat_range, time_range,
               filter = filter,
))
```

Currently only POST search requests are supported.
