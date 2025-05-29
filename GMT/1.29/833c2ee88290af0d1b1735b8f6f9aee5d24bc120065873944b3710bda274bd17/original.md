```
getprovider(name, zoom::Int; variant="", date::String="", key::String="")
```

Get information about a tile provider given its name and zoom level. The returned information is only relevant for internal use and is an implementation detail not documented here.

### Arguments

  * `name`: Name of the tile provider. Currently available are "Bing" (the default), "Google", "OSM", "Esri", "Nimbo". Optionally, the `name` can be a tuple of two strings, where the first string is the provider name and the second string is the variant name (see the `variant` bellow).
  * The `name` argument can also be a `Provider` type from the TileProviders.jl package. For example, after importing TileProviders.jl, $provider = NASAGIBSTimeseries()$ and next pass it to `getprovider`.
  * `date`: Currently only used with the 'Nimbo' provider. Pass date in 'YYYY_MM' or 'YYYY,MM' format.
  * `key`: Currently only used with the 'Nimbo' provider. Pass your https://nimbo.earth/ API key.
  * `zoom`: Requested zoom level. Will be capped at the provider's maximum.
  * `variant`: Optional variant for providers with multiple map layers.

      * `Bing`: variants => "Aerial" (default), "Road", or "Hybrid".
      * `Google`: variants => "Satellite", "Road", "Terrain", or "Hybrid".
      * `Esri`: variants => "World_Street_Map" (default), "Elevation/World_Hillshade", or "World_Imagery".
      * `Nimbo`: variants => "RGB" (default), "NIR", "NDVI", or "RADAR".
