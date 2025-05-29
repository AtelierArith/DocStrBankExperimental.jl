```
Traj{T1 <: Signed, T2 <: AbstractFloat}
```

Trajectory struct, i.e., GPS or other truth flight data. Subtype of `Path`.

| **Field** | **Type**      | **Description**                                                  |
|:--------- |:------------- |:---------------------------------------------------------------- |
| `N`       | `T1`          | number of samples (instances)                                    |
| `dt`      | `T2`          | measurement time step [s]                                        |
| `tt`      | Vector{`T2`}  | time [s]                                                         |
| `lat`     | Vector{`T2`}  | latitude  [rad]                                                  |
| `lon`     | Vector{`T2`}  | longitude [rad]                                                  |
| `alt`     | Vector{`T2`}  | altitude  [m]                                                    |
| `vn`      | Vector{`T2`}  | north velocity [m/s]                                             |
| `ve`      | Vector{`T2`}  | east  velocity [m/s]                                             |
| `vd`      | Vector{`T2`}  | down  velocity [m/s]                                             |
| `fn`      | Vector{`T2`}  | north specific force [m/s]                                       |
| `fe`      | Vector{`T2`}  | east  specific force [m/s]                                       |
| `fd`      | Vector{`T2`}  | down  specific force [m/s]                                       |
| `Cnb`     | Array{`T2,3`} | `3` x `3` x `N` direction cosine matrix (body to navigation) [-] |
