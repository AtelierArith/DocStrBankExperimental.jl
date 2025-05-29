```
CRLBout{T2 <: AbstractFloat}
```

Cramér–Rao lower bound extracted output struct.

| **Field**  | **Type**     | **Description**                 |
|:---------- |:------------ |:------------------------------- |
| `lat_std`  | Vector{`T2`} | latitude  1-σ [rad]             |
| `lon_std`  | Vector{`T2`} | longitude 1-σ [rad]             |
| `alt_std`  | Vector{`T2`} | altitude  1-σ [m]               |
| `vn_std`   | Vector{`T2`} | north velocity 1-σ [m/s]        |
| `ve_std`   | Vector{`T2`} | east  velocity 1-σ [m/s]        |
| `vd_std`   | Vector{`T2`} | down  velocity 1-σ [m/s]        |
| `tn_std`   | Vector{`T2`} | north tilt (attitude) 1-σ [rad] |
| `te_std`   | Vector{`T2`} | east  tilt (attitude) 1-σ [rad] |
| `td_std`   | Vector{`T2`} | down  tilt (attitude) 1-σ [rad] |
| `fogm_std` | Vector{`T2`} | FOGM 1-σ [nT]                   |
| `n_std`    | Vector{`T2`} | northing 1-σ [m]                |
| `e_std`    | Vector{`T2`} | easting  1-σ [m]                |
