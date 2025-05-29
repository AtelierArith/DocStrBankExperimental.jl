```
encode(lon, lat, precision, bits_per_char = 2)
```

Encode a longitude-latitude pair as a geohash string. The length of the resulting geohash is `precision`, so higher `precision` gives a finer grained encoding. Return the geohash string.

# Arguments

  * `lon::Real`: longitude in degrees of point to encode. Must be in [-180,180].
  * `lat::Real`: latitude in degrees of point to encode. Must be in [-90,90].
  * `precision::Integer`: precision of returned geohash. Must be positive.
  * `bits_per_char ∈ [2,4,6]`: how many bits of information each character encodes.

!!! note
    To avoid overflow in machine arithmetic, `precision * bits_per_char` must be <= 62. This still allows meter-level granularity. If your use case requires sub-meter granularity, you may wish to reconsider using longitude-latitude coordinates.

