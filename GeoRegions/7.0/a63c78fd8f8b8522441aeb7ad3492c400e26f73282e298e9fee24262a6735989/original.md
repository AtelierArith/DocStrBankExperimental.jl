```
on(
    point :: Point2{<:Real},
    geo   :: GeoRegion;
    throw :: Bool = false
) -> tf :: Bool
```

Check if a geographical point `point` is on the boundary of a shape of a GeoRegion defined by `geo`.

# Arguments

  * `point` : A geographical point of Type `Point`.  Pass `Point(plon,plat)`, where `plon` and `plat` are the longitude and latitudes of the point.
  * `geo`   : The GeoRegion struct container.

# Keyword Arguments

  * `throw` : If `true`, then if `point` is not within `geo`, an error is thrown and the program stops running.

# Returns

  * `tf` : A `true`/`false` boolean.
