```
isinERA5Region(
    geo    :: GeoRegion,
    e5geo  :: ERA5Region;
    domask :: Bool = false,
    throw  :: Bool = true
) -> Bool
```

Check if a child GeoRegion defined by `geo` is within a ERA5Region `e5geo`.

# Arguments

  * `geo`   : A GeoRegion that we postulate to be a "child", or a subset of the ERA5Region defined by `e5geo`
  * `e5geo` : An ERA5Region that we postulate to be a "parent", or containing the GeoRegion defined by `geo`

# Keyword Arguments

  * `throw`  : If `true`, then if `geo` is not within `e5geo`, an error is thrown and the program stops running
  * `domask` : If `throw` is `false` and `domask` is `true`, return a mask (with bounds defined by the `geo` GeoRegion) showing the region where `geo` and `e5geo` do not overlap
