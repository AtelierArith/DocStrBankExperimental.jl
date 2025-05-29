```
tableGeoRegions(;
    path :: AbstractString = homedir(),
    predefined :: Bool = true,
    custom     :: Bool = true,
    warn :: Bool = true,
    crop :: Bool = false
) -> nothing
```

Display all available GeoRegions in tabular format.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `predefined` : If `true`, predefined Giorgi, SREX and IPPC AR6 list of GeoRegions will be displayed.
  * `custom` : If `true`, custom, user-defined list of GeoRegions will be displayed.
  * `warn` : If `true`, display warnings if custom files do not exist.
  * `crop` : If `true`, will crop the vertical extent of the table, default is `false`.
