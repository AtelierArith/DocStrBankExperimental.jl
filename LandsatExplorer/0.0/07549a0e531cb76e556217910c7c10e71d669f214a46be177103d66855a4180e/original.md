```
search(satellite, level; dates=nothing, clouds=nothing, geom=nothing, max_results=100)
```

Search for Landsat scenes belonging to the given satellite and processing level.

# Parameters

  * `satellite`: One of `"LANDSAT_5"`, `"LANDSAT_7"`, or "`LANDSAT_8"`, or "`LANDSAT_9"`.
  * `level`: The processing level; either 1 or 2.

# Keywords

  * `dates`: The date range for image acquisition. Should be a tuple of `DateTime` objects.
  * `clouds`: The maximum allowable cloud cover as a percentage.
  * `geom`: A geometry specifying the region of interest. Can be a `Point`, `BoundingBox`, or any other `GeoInterface` compatible geometry.
  * `max_results`: The maximum number of results to return (default = 100).

# Returns

A `DataFrame` with the columns `:Name`, `:AcquisitionDate`, `:PublicationDate`, `:CloudCover`, and `:Id`.

# Example

```julia
julia> p = Point(52.0, -114.2);

julia> dates = (DateTime(2020, 8, 1), DateTime(2020, 9, 1));

julia> search("LANDSAT_8", 2, dates=dates, geom=p, clouds=21)
3×5 DataFrame
 Row │ Name                               AcquisitionDate      Pub ⋯
     │ String                             String               Str ⋯
─────┼──────────────────────────────────────────────────────────────
   1 │ LC08_L2SP_043024_20200818_202008…  2020-08-18 00:00:00  202 ⋯
   2 │ LC08_L2SP_042024_20200811_202009…  2020-08-11 00:00:00  202
   3 │ LC08_L2SP_043024_20200802_202009…  2020-08-02 00:00:00  202
                                                   3 columns omitted
```
