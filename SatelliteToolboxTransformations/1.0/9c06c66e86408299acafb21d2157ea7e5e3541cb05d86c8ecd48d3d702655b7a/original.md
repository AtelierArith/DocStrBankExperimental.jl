```
ecef_to_geocentric(r_e::AbstractVector{T}) -> NTuple{3, T}
```

Convert the vector `r_e` represented in the Earth-Centered, Earth-Fixed (ECEF) reference frame into geocentric coordinates (geocentric latitude, longitude, and distance from Earth's center).

# Returns

  * `T`: Geocentric latitude [rad] ∈ [-π / 2, π / 2].
  * `T`: Longitude [rad] ∈ [-π , π].
  * `T`: Distance from Earth's center [m].
