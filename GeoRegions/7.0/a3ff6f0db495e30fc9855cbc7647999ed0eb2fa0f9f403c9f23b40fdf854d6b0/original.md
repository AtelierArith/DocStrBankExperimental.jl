```
coordinates(
    geo :: GeoRegion;
    n :: Int = 1
) -> lon :: Vector{<:Real}, lat :: Vector{<:Real}
```

For a given GeoRegion, create longitude and latitude vectors of the shape.

# Arguments

  * `geo` : A GeoRegion.
  * `n` : The number of segments on each side of the shape.

# Returns

  * `lon` : A vector of longitude points for the shape of the GeoRegion.
  * `lat` : A vector of latitude points for the shape of the GeoRegion.
