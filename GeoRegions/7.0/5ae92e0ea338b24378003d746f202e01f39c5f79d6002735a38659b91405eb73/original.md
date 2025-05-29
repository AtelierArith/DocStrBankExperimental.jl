```
PolyRegion(
    ID   :: AbstractString,
    pID  :: AbstractString,
    name :: AbstractString,
    lon  :: Vector{<:Real},
    lat  :: Vector{<:Real};
    join :: Bool = true,
    save :: Bool = false,
    path :: AbstractString = pwd(),
    verbose :: Bool = false,
    ST = String,
    FT = Float64
) -> geo :: PolyRegion{ST,FT}
```

Creates a polygonal GeoRegion.

# Arguments

  * `ID` : The keyword ID that will be used to identify the GeoRegion.           If the ID is already in use, then an error will be thrown.
  * `pID` : The ID of the parent GeoRegion where information can be extracted from.
  * `name` : A name for the GeoRegion (meta information, can be used in Logging).
  * `lon` : A vector containing the longitude points.
  * `lat` : A vector containing the latitude points.

# Keyword Arguments

  * `join` : If `true`, if the first and last coordinate points do not match, append the first coordinate again to close the shape.
  * `save` : If `true`, save the GeoRegion into the list of custom GeoRegions in the path specified by `path`.
  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `verbose` : If `true`, verbose logging for ease of monitoring. Default is `false`.

# Returns

  * `geo` : A polygonal GeoRegion.
