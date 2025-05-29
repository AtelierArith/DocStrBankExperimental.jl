```
rmID(
    ID :: AbstractString;
    path :: AbstractString = geodir
) -> nothing
```

Removes any GeoRegion associated with the ID `ID`. ID must be exact.

# Arguments

  * `ID` : The keyword ID that will be used to identify the GeoRegion.           If the ID is not valid (i.e. not being used), then an error will be thrown.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the home directory `homedir()`.
