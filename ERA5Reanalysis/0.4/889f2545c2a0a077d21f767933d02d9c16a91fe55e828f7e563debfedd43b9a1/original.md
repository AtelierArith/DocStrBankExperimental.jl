```
isinERA5Region(
    point :: Point2{<:Real},
    e5geo :: ERA5Region;
    tlon  :: Real = 0,
    tlat  :: Real = 0,
    throw :: Bool = true
) -> Bool
```

Check if a geographical point `Point` is within an ERA5Region defined by `e5geo`.

# Arguments

  * `point` : A geographical point of Type `Point2`.  Pass `Point2(plon,plat)`, where `plon` and `plat` are the longitude and latitudes of the point.
  * `e5geo` : The ERA5Region struct container

# Keyword Arguments

  * `tlon`  : Threshold for the longitude bound
  * `tlat`  : Threshold for the latitude bound
  * `throw` : If `true`, then if `Point` is not within `geo`, an error is thrown and the program stops running.
