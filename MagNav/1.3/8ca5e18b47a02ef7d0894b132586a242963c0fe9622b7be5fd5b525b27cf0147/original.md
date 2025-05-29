```
XYZ21{T1 <: Signed, T2 <: AbstractFloat} <: XYZ{T1, T2}
```

Subtype of `XYZ` for 2021 SGL datasets.

| **Field**   | **Type**        | **Description**                                                           |
|:----------- |:--------------- |:------------------------------------------------------------------------- |
| `info`      | String          | dataset information                                                       |
| `traj`      | Traj{`T1`,`T2`} | trajectory struct                                                         |
| `ins`       | INS{`T1`,`T2`}  | inertial navigation system struct                                         |
| `flux_a`    | MagV{`T2`}      | Flux A vector magnetometer measurement struct                             |
| `flux_b`    | MagV{`T2`}      | Flux B vector magnetometer measurement struct                             |
| `flux_c`    | MagV{`T2`}      | Flux C vector magnetometer measurement struct                             |
| `flux_d`    | MagV{`T2`}      | Flux D vector magnetometer measurement struct                             |
| `flight`    | Vector{`T2`}    | flight number(s)                                                          |
| `line`      | Vector{`T2`}    | line number(s), i.e., segments within `flight`                            |
| `year`      | Vector{`T2`}    | year                                                                      |
| `doy`       | Vector{`T2`}    | day of year                                                               |
| `utm_x`     | Vector{`T2`}    | x-coordinate, WGS-84 UTM zone 18N [m]                                     |
| `utm_y`     | Vector{`T2`}    | y-coordinate, WGS-84 UTM zone 18N [m]                                     |
| `utm_z`     | Vector{`T2`}    | z-coordinate, GPS altitude above WGS-84 ellipsoid [m]                     |
| `msl`       | Vector{`T2`}    | z-coordinate, GPS altitude above EGM2008 Geoid [m]                        |
| `baro`      | Vector{`T2`}    | barometric altimeter [m]                                                  |
| `diurnal`   | Vector{`T2`}    | measured diurnal, i.e., temporal variations or space weather effects [nT] |
| `igrf`      | Vector{`T2`}    | International Geomagnetic Reference Field (IGRF), i.e., core field [nT]   |
| `mag_1_c`   | Vector{`T2`}    | Mag 1 compensated (clean) scalar magnetometer measurements [nT]           |
| `mag_1_uc`  | Vector{`T2`}    | Mag 1 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_2_uc`  | Vector{`T2`}    | Mag 2 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_3_uc`  | Vector{`T2`}    | Mag 3 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_4_uc`  | Vector{`T2`}    | Mag 4 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_5_uc`  | Vector{`T2`}    | Mag 5 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `cur_com_1` | Vector{`T2`}    | current sensor: aircraft radio 1 [A]                                      |
| `cur_ac_hi` | Vector{`T2`}    | current sensor: air conditioner fan high [A]                              |
| `cur_ac_lo` | Vector{`T2`}    | current sensor: air conditioner fan low [A]                               |
| `cur_tank`  | Vector{`T2`}    | current sensor: cabin fuel pump [A]                                       |
| `cur_flap`  | Vector{`T2`}    | current sensor: flap motor [A]                                            |
| `cur_strb`  | Vector{`T2`}    | current sensor: strobe lights [A]                                         |
| `vol_block` | Vector{`T2`}    | voltage sensor: block [V]                                                 |
| `vol_back`  | Vector{`T2`}    | voltage sensor: backplane [V]                                             |
| `vol_cabt`  | Vector{`T2`}    | voltage sensor: cabinet [V]                                               |
| `vol_fan`   | Vector{`T2`}    | voltage sensor: cooling fan [V]                                           |
| `aux_1`     | Vector{`T2`}    | flexible-use auxiliary data 1                                             |
| `aux_2`     | Vector{`T2`}    | flexible-use auxiliary data 2                                             |
| `aux_3`     | Vector{`T2`}    | flexible-use auxiliary data 3                                             |
