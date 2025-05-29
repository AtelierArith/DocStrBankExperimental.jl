```
in(
    cgeo :: GeoRegion,
    geo  :: GeoRegion;
    n    :: Int = 100,
    throw   :: Bool = false,
    verbose :: Bool = false
) -> tf :: Bool
```

Check if a child GeoRegion defined by `cgeo` is within another GeoRegion `geo`.

# Arguments

  * `cgeo` : A GeoRegion that we postulate to be a "child", or a subset of the GeoRegion defined by `geo`.
  * `geo` : A GeoRegion that we postulate to be a "parent", or containing the GeoRegion defined by `cgeo`.

# Keyword Arguments

  * `n` : The number of segments to split each of the `GeoRegion`s into. Default is 100.
  * `throw`  : If `true`, then if `cgeo` is not within `geo`, an error is thrown and the program stops running.
  * `verbose` : If `true`, print logs to screen.

# Returns

  * `tf` : A `true`/`false` boolean.
