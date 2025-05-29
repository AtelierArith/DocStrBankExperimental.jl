```
isequal(
    geo1 :: GeoRegion,
    geo2 :: GeoRegion;
    strict  :: Bool = true,
    verbose :: Bool = false
) -> tf :: Bool
```

Checks all the fields (except names) of two different GeoRegions in order to determine if they are exactly the same. The GeoRegions need not be of the same GeoRegion `type` as long as they have the same `ID`, `pID` and area defined by `shape`.

The `geo1.shape` and `geo2.shape` need not be exactly the same as long as they define exactly the same area (i.e., the points in `geo2` can be a `circshift()` version of `geo1`).

# Arguments

  * `geo1` : The first GeoRegion.
  * `geo2` : The second GeoRegion.

# Keyword Arguments

  * `strict` : If `true` (which is default), `geo1` and `geo2` must be of the same GeoRegion `type` (e.g., a `RectRegion ≠ PolyRegion`).
  * `verbose` : Verbose logging for ease of monitoring? Default is `false`.

# Returns

  * `tf` : A `true`/`false` boolean.
