```
search(satellite; product=nothing, dates=nothing, tile=nothing, clouds=nothing, geom=nothing, max_results=100)
```

Search for satellite images matching the provided filters.

# Parameters

  * `satellite`: One of "SENTINEL-1", "SENTINEL-2", or "SENTINEL-3".

# Keywords

  * `product`: The product type to search for such as "L2A", "L1C", "GRD", etc.
  * `dates`: The date range for image acquisition. Should be a tuple of `DateTime` objects.
  * `tile`: Restrict results to a given tile. Only available for Sentinel-2.
  * `clouds`: The maximum allowable cloud cover as a percentage. Not available for Sentinel-1.
  * `geom`: A geometry specifying the region of interest. Can be a `Point`, `BoundingBox`, or any other `GeoInterface` compatible geometry.
  * `max_results`: The maximum number of results to return (default = 100).

# Returns

A `DataFrame` with the columns `:Name`, `:AcquisitionDate`, `:PublicationDate`, `:CloudCover`, and `:Id`.

# Example

```julia
julia> geom = GeoDataFrames.read("test/data/roi.geojson").geometry[1];

julia> dates = (DateTime(2020, 8, 4), DateTime(2020, 8, 5));

julia> search("SENTINEL-2",  geom=geom, dates=dates)
3×5 DataFrame
 Row │ Name                               AcquisitionDate           Pub ⋯
     │ String                             String                    Str ⋯
─────┼───────────────────────────────────────────────────────────────────
   1 │ S2B_MSIL2A_20200804T183919_N0500…  2020-08-04T18:39:19.024Z  202 ⋯
   2 │ S2B_MSIL1C_20200804T183919_N0209…  2020-08-04T18:39:19.024Z  202
   3 │ S2B_MSIL1C_20200804T183919_N0500…  2020-08-04T18:39:19.024Z  202
                                                        3 columns omitted
```
