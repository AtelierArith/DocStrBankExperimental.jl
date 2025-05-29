```
overwrite(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    verbose :: Bool = false
) -> nothing
```

Overwrites preexisting information associated with the ID `geo.ID` in `path`, with new information from the `GeoRegion` specified by `geo`.

# Arguments

  * `geo` : The GeoRegion to be saved into the custom lists in `path`, overwriting any preexisting information associated with the ID `geo.ID`.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the `local` package variable `geodir`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.
