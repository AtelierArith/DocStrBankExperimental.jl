```
addGeoRegions(
    fname :: AbstractString;
    path  :: AbstractString = pwd(),
    overwrite :: Bool = false,
    verbose   :: Bool = false
) -> nothing
```

Add GeoRegions from the file `fname` into the project directory defined by `path`.

# Arguments

  * `fname` : name + path of the file containing GeoRegion information.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the current working directory `pwd()`.
  * `overwrite` : If `true`, override any custom GeoRegions that have the same `ID`s as those in the file `fname`.
