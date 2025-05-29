```
TiltRegion(
    ID   :: AbstractString,
    pID  :: AbstractString,
    name :: AbstractString,
    X    :: Real,
    Y    :: Real,
    ΔX   :: Real,
    ΔY   :: Real,
    θ    :: Real;
    save :: Bool = false,
    path :: AbstractString = pwd(),
    verbose :: Bool = false,
    ST = String,
    FT = Float64
) -> geo :: TiltRegion{ST,FT}
```

Creates a tilted rectangular GeoRegion.

# Arguments

  * `ID` : The keyword ID that will be used to identify the GeoRegion.           If the ID is already in use, then an error will be thrown.
  * `pID` : The ID of the parent GeoRegion where information can be extracted from.
  * `name` : A name for the GeoRegion (meta information, can be used in Logging).
  * `X`  : Longitude coordinate of region centre.
  * `Y`  : Latitude coordinate of region centre.
  * `ΔX` : Half-width in longitude coordinates (before tilting).
  * `ΔY` : Half-width in latitude coordinates (before tilting).
  * `θ`  : Tilt of rectangular region in **degrees**.

# Keyword Arguments

  * `save` : If `true`, save the GeoRegion into the list of custom GeoRegions in the path specified by `path`.
  * `path` : The path where the list of custom GeoRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `geo` : A tilted rectangular GeoRegion.
