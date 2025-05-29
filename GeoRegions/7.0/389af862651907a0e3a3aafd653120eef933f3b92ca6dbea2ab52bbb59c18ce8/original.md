```
add(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    verbose :: Bool = false
) -> nothing
```

Saves information on the GeoRegion `geo` to a directory specified by `path`.

# Arguments

  * `geo` : The GeoRegion to be saved into the custom lists in `path`.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the `local` package variable `geodir`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.
