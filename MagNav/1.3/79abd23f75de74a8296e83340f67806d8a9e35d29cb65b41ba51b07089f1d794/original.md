```
FILTout{T1 <: Signed, T2 <: AbstractFloat} <: Path{T1, T2}
```

Filter extracted output struct. Subtype of `Path`.

| **Field**  | **Type**     | **Description**                                    |
|:---------- |:------------ |:-------------------------------------------------- |
| `N`        | `T1`         | number of samples (instances)                      |
| `dt`       | `T2`         | measurement time step [s]                          |
| `tt`       | Vector{`T2`} | time [s]                                           |
| `lat`      | Vector{`T2`} | latitude  [rad]                                    |
| `lon`      | Vector{`T2`} | longitude [rad]                                    |
| `alt`      | Vector{`T2`} | altitude  [m]                                      |
| `vn`       | Vector{`T2`} | north velocity [m/s]                               |
| `ve`       | Vector{`T2`} | east  velocity [m/s]                               |
| `vd`       | Vector{`T2`} | down  velocity [m/s]                               |
| `tn`       | Vector{`T2`} | north tilt (attitude) [rad]                        |
| `te`       | Vector{`T2`} | east  tilt (attitude) [rad]                        |
| `td`       | Vector{`T2`} | down  tilt (attitude) [rad]                        |
| `ha`       | Vector{`T2`} | barometer aiding altitude [m]                      |
| `ah`       | Vector{`T2`} | barometer aiding vertical acceleration [m/s^2]     |
| `ax`       | Vector{`T2`} | x accelerometer [m/s^2]                            |
| `ay`       | Vector{`T2`} | y accelerometer [m/s^2]                            |
| `az`       | Vector{`T2`} | z accelerometer [m/s^2]                            |
| `gx`       | Vector{`T2`} | x gyroscope [rad/s]                                |
| `gy`       | Vector{`T2`} | y gyroscope [rad/s]                                |
| `gz`       | Vector{`T2`} | z gyroscope [rad/s]                                |
| `fogm`     | Vector{`T2`} | FOGM catch-all [nT]                                |
| `lat_std`  | Vector{`T2`} | latitude  1-σ [rad]                                |
| `lon_std`  | Vector{`T2`} | longitude 1-σ [rad]                                |
| `alt_std`  | Vector{`T2`} | altitude  1-σ [m]                                  |
| `vn_std`   | Vector{`T2`} | north velocity 1-σ [m/s]                           |
| `ve_std`   | Vector{`T2`} | east  velocity 1-σ [m/s]                           |
| `vd_std`   | Vector{`T2`} | down  velocity 1-σ [m/s]                           |
| `tn_std`   | Vector{`T2`} | north tilt (attitude) 1-σ [rad]                    |
| `te_std`   | Vector{`T2`} | east  tilt (attitude) 1-σ [rad]                    |
| `td_std`   | Vector{`T2`} | down  tilt (attitude) 1-σ [rad]                    |
| `ha_std`   | Vector{`T2`} | barometer aiding altitude 1-σ [m]                  |
| `ah_std`   | Vector{`T2`} | barometer aiding vertical acceleration 1-σ [m/s^2] |
| `ax_std`   | Vector{`T2`} | x accelerometer 1-σ [m/s^2]                        |
| `ay_std`   | Vector{`T2`} | y accelerometer 1-σ [m/s^2]                        |
| `az_std`   | Vector{`T2`} | z accelerometer 1-σ [m/s^2]                        |
| `gx_std`   | Vector{`T2`} | x gyroscope 1-σ [rad/s]                            |
| `gy_std`   | Vector{`T2`} | y gyroscope 1-σ [rad/s]                            |
| `gz_std`   | Vector{`T2`} | z gyroscope 1-σ [rad/s]                            |
| `fogm_std` | Vector{`T2`} | FOGM catch-all 1-σ [nT]                            |
| `n_std`    | Vector{`T2`} | northing 1-σ [m]                                   |
| `e_std`    | Vector{`T2`} | easting  1-σ [m]                                   |
| `lat_err`  | Vector{`T2`} | latitude  error [rad]                              |
| `lon_err`  | Vector{`T2`} | longitude error [rad]                              |
| `alt_err`  | Vector{`T2`} | altitude  error [m]                                |
| `vn_err`   | Vector{`T2`} | north velocity error [m/s]                         |
| `ve_err`   | Vector{`T2`} | east  velocity error [m/s]                         |
| `vd_err`   | Vector{`T2`} | down  velocity error [m/s]                         |
| `tn_err`   | Vector{`T2`} | north tilt (attitude) error [rad]                  |
| `te_err`   | Vector{`T2`} | east  tilt (attitude) error [rad]                  |
| `td_err`   | Vector{`T2`} | down  tilt (attitude) error [rad]                  |
| `n_err`    | Vector{`T2`} | northing error [m]                                 |
| `e_err`    | Vector{`T2`} | easting  error [m]                                 |
