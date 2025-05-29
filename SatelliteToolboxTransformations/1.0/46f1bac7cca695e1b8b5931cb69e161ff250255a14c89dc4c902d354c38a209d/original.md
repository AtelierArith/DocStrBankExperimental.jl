```
geocentric_to_ecef(lat::Number, lon::Number, r::Number) -> SVector{3, T}
```

Convert the geocentric coordinates (latitude `lat` [rad], longitude `lon` [rad], and distance from Earth's center `r` [m]) into a Earth-Centered, Earth-Fixed vector [m].

!!! note
    The output type `T` is obtained by promoting the input types `T1`, `T2`, and `T3`. If all of them are integers, they will be converted to float.

