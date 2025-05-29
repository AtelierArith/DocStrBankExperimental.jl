```
on(
    geo1 :: GeoRegion,
    geo2 :: GeoRegion;
    n    :: Int = 2,
    throw   :: Bool = false,
    verbose :: Bool = false
) -> tf :: Bool
```

Check if the GeoRegions `geo1` and `geo2` have the same shape. The order of `geo1` and `geo2` does not matter.

# Arguments

  * `geo1` : The first GeoRegion
  * `geo2` : The second GeoRegion

# Keyword Arguments

  * `n` : The number of segments to split each of the `GeoRegion`s into. Default is 2.
  * `throw` : If `true`, then if `geo1` does not have the same shape as `geo2`, an error is thrown and the program stops running.
  * `verbose` : If `true`, print logs to screen.

# Returns

  * `tf` : A `true`/`false` boolean.
