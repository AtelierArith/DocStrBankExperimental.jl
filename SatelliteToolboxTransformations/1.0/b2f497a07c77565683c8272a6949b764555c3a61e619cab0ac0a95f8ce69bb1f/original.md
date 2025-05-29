```
geocentric_to_ecef(geocentric_state::AbstractVector) -> SVector{3, T}
```

Convert the geocentric coordinates (latitude `lat` [rad], longitude `lon` [rad], and distance from Earth's center `r` [m]) into a Earth-Centered, Earth-Fixed vector [m].
