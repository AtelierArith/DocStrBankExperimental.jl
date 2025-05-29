```
XYZ1{T1 <: Signed, T2 <: AbstractFloat} <: XYZ{T1, T2}
```

Subtype of `XYZ` containing a flexible dataset for future use. NaNs may be used in place of any unused fields (e.g., `aux_3`) when creating struct.

| **Field**  | **Type**        | **Description**                                                           |
|:---------- |:--------------- |:------------------------------------------------------------------------- |
| `info`     | String          | dataset information                                                       |
| `traj`     | Traj{`T1`,`T2`} | trajectory struct                                                         |
| `ins`      | INS{`T1`,`T2`}  | inertial navigation system struct                                         |
| `flux_a`   | MagV{`T2`}      | Flux A vector magnetometer measurement struct                             |
| `flux_b`   | MagV{`T2`}      | Flux B vector magnetometer measurement struct                             |
| `flight`   | Vector{`T2`}    | flight number(s)                                                          |
| `line`     | Vector{`T2`}    | line number(s), i.e., segments within `flight`                            |
| `year`     | Vector{`T2`}    | year                                                                      |
| `doy`      | Vector{`T2`}    | day of year                                                               |
| `diurnal`  | Vector{`T2`}    | measured diurnal, i.e., temporal variations or space weather effects [nT] |
| `igrf`     | Vector{`T2`}    | International Geomagnetic Reference Field (IGRF), i.e., core field [nT]   |
| `mag_1_c`  | Vector{`T2`}    | Mag 1 compensated (clean) scalar magnetometer measurements [nT]           |
| `mag_2_c`  | Vector{`T2`}    | Mag 2 compensated (clean) scalar magnetometer measurements [nT]           |
| `mag_3_c`  | Vector{`T2`}    | Mag 3 compensated (clean) scalar magnetometer measurements [nT]           |
| `mag_1_uc` | Vector{`T2`}    | Mag 1 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_2_uc` | Vector{`T2`}    | Mag 2 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_3_uc` | Vector{`T2`}    | Mag 3 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `aux_1`    | Vector{`T2`}    | flexible-use auxiliary data 1                                             |
| `aux_2`    | Vector{`T2`}    | flexible-use auxiliary data 2                                             |
| `aux_3`    | Vector{`T2`}    | flexible-use auxiliary data 3                                             |
