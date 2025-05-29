```
isgeoshape(
    lon  :: Vector{<:Real},
    lat  :: Vector{<:Real};
    path :: AbstractString = dirname(geo.path),
    returnID :: Bool = true,
    verbose  :: Bool = false
) -> tf :: Bool
```

Checks all the GeoRegions defined in the project determined by `path`. If there exists a `GeoRegion` with the same shape as defined by the vectors `lon` and `lat`, returns `true` by default, or otherwise, if `returnID` is true, it will return the ID. If there is no `GeoRegion` with the same shape, then either returns a `false` or throws and error depending on `throw`

# Arguments

  * `lon` : Vector of longitude points.
  * `lat` : Vector of latitude points.

# Keyword Arguments

  * `path` : The path where GeoRegions will be retrieved from and compared against.          Defaults to the directory `homedir()`.
  * `returnID` : If `true`, then returns the `ID` of the `GeoRegion` in `path` with the same shape as `geo`.
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `tf` : A `true`/`false` boolean.
