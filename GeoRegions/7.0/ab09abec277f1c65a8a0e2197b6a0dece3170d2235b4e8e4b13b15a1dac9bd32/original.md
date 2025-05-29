```
rm(
    geo  :: GeoRegion;
    path :: AbstractString = geodir
) -> nothing
```

Removes the GeoRegion `geo` from the custom lists specified in `path`. The GeoRegion must have exactly the same properties as the one in the custom list.

# Arguments

  * `geo` : The GeoRegion to be removed from the custom lists in `path`.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the `local` package variable `geodir`.
