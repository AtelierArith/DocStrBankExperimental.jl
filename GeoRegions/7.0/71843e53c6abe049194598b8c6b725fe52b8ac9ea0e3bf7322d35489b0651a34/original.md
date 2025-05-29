```
==(
    geo1 :: GeoRegion,
    geo2 :: GeoRegion,
) -> tf :: Bool
```

Checks all the fields (except names and paths) of two different GeoRegions in order to determine if they are exactly the same. The GeoRegions must be of the same GeoRegion `type`.

The `geo1.shape` and `geo2.shape` need not be exactly the same as long as they define the same area (i.e., the points in `geo2` can be a circshift version of `geo1`).

# Arguments

  * `geo1` : The first GeoRegion.
  * `geo2` : The second GeoRegion.

# Returns

  * `tf` : A `true`/`false` boolean.
