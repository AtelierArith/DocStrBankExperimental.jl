```
isID(
    ID   :: AbstractString;
    path :: AbstractString = homedir(),
    throw   :: Bool = true,
    verbose :: Bool = false
) -> tf :: Bool
```

Checks if there is a GeoRegion, that exists in the custom lists defined in `path`, with the ID `ID`.

# Arguments

  * `ID` : The keyword ID that will be used to identify the GeoRegion.       If the ID is not valid (i.e. not being used), then an error will be thrown.

# Keyword Arguments

  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the current directory `pwd()`.
  * `throw` : If `true`, then throws an error if `ID` is not a valid `GeoRegion` identifier instead of returning the Boolean `tf`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `tf` : A `true`/`false` boolean.
