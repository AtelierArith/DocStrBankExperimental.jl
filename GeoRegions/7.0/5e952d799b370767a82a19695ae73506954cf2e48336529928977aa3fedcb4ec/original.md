```
GeoRegion(
    ID :: AbstractString;
    path    :: AbstractString = homedir(),
    verbose :: Bool = false
) -> geo :: GeoRegion
```

Extracts information of the GeoRegion with the ID `ID`.  If no GeoRegion with this ID exists, an error is thrown.

# Arguments

  * `ID` : The ID that will be used to identify the GeoRegion.           If the ID is not valid (i.e. not being used), then an error will be thrown.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `geo` : A GeoRegion.
