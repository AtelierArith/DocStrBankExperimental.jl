```
RectRegion(
    ID    :: AbstractString,
    pID   :: AbstractString,
    name  :: AbstractString,
    bound :: Vector{<:Real};
    save :: Bool = false,
    path :: AbstractString = pwd(),
    verbose :: Bool = false,
    ST = String,
    FT = Float64
) -> geo :: RectRegion{ST,FT}
```

Creates a rectilinear GeoRegion.

# Arguments

  * `ID` : The keyword ID that will be used to identify the GeoRegion.           If the ID is already in use, then an error will be thrown.
  * `pID` : The ID of the parent GeoRegion where information can be extracted from.
  * `name` : A name for the GeoRegion (meta information, can be used in Logging).
  * `bound` : The [N,S,E,W] coordinates defining the region.

# Keyword Arguments

  * `save` : If `true`, save the GeoRegion into the list of custom GeoRegions in the path specified by `path`.
  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `geo` : A rectilinear GeoRegion.
