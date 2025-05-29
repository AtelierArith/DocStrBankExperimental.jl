```
INSout{T2 <: AbstractFloat}
```

Inertial navigation system extracted output struct.

| **Field** | **Type**     | **Description**       |
|:--------- |:------------ |:--------------------- |
| `lat_std` | Vector{`T2`} | latitude  1-σ [rad]   |
| `lon_std` | Vector{`T2`} | longitude 1-σ [rad]   |
| `alt_std` | Vector{`T2`} | altitude  1-σ [m]     |
| `n_std`   | Vector{`T2`} | northing  1-σ [m]     |
| `e_std`   | Vector{`T2`} | easting   1-σ [m]     |
| `lat_err` | Vector{`T2`} | latitude  error [rad] |
| `lon_err` | Vector{`T2`} | longitude error [rad] |
| `alt_err` | Vector{`T2`} | altitude  error [m]   |
| `n_err`   | Vector{`T2`} | northing  error [m]   |
| `e_err`   | Vector{`T2`} | easting   error [m]   |
