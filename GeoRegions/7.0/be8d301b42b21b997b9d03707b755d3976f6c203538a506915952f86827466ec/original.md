```
isgeo(
    geo  :: GeoRegion;
    path :: AbstractString = dirname(geo.path),
    strict  :: Bool = true,
    throw   :: Bool = true,
    verbose :: Bool = false
) -> tf :: Bool
```

Checks all the GeoRegions defined in the project determined by `path`. If there exists a `GeoRegion` with the same `ID` **and** the same field values (except `name` and `path`) as the GeoRegion `geo`, returns `true`. Otherwise, returns `false` or throws an error.

# Arguments

  * `geo` : The GeoRegion in question.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the directory `geo.path`.
  * `strict` : If `true` (which is default), check to see if all fields are equivalent except for `name` and `path`.
  * `throw` : If `true`, then throws an error if there is no `GeoRegion` defined in `path` with the same characteristics or field values as `geo`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `tf` : A `true`/`false` boolean.
