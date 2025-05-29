```
XYZ20{T1 <: Signed, T2 <: AbstractFloat} <: XYZ{T1, T2}
```

Subtype of `XYZ` for 2020 SGL datasets.

| **Field**    | **Type**        | **Description**                                                           |
|:------------ |:--------------- |:------------------------------------------------------------------------- |
| `info`       | String          | dataset information                                                       |
| `traj`       | Traj{`T1`,`T2`} | trajectory struct                                                         |
| `ins`        | INS{`T1`,`T2`}  | inertial navigation system struct                                         |
| `flux_a`     | MagV{`T2`}      | Flux A vector magnetometer measurement struct                             |
| `flux_b`     | MagV{`T2`}      | Flux B vector magnetometer measurement struct                             |
| `flux_c`     | MagV{`T2`}      | Flux C vector magnetometer measurement struct                             |
| `flux_d`     | MagV{`T2`}      | Flux D vector magnetometer measurement struct                             |
| `flight`     | Vector{`T2`}    | flight number(s)                                                          |
| `line`       | Vector{`T2`}    | line number(s), i.e., segments within `flight`                            |
| `year`       | Vector{`T2`}    | year                                                                      |
| `doy`        | Vector{`T2`}    | day of year                                                               |
| `utm_x`      | Vector{`T2`}    | x-coordinate, WGS-84 UTM zone 18N [m]                                     |
| `utm_y`      | Vector{`T2`}    | y-coordinate, WGS-84 UTM zone 18N [m]                                     |
| `utm_z`      | Vector{`T2`}    | z-coordinate, GPS altitude above WGS-84 ellipsoid [m]                     |
| `msl`        | Vector{`T2`}    | z-coordinate, GPS altitude above EGM2008 Geoid [m]                        |
| `baro`       | Vector{`T2`}    | barometric altimeter [m]                                                  |
| `diurnal`    | Vector{`T2`}    | measured diurnal, i.e., temporal variations or space weather effects [nT] |
| `igrf`       | Vector{`T2`}    | International Geomagnetic Reference Field (IGRF), i.e., core field [nT]   |
| `mag_1_c`    | Vector{`T2`}    | Mag 1 compensated (clean) scalar magnetometer measurements [nT]           |
| `mag_1_lag`  | Vector{`T2`}    | Mag 1 lag-corrected scalar magnetometer measurements [nT]                 |
| `mag_1_dc`   | Vector{`T2`}    | Mag 1 diurnal-corrected scalar magnetometer measurements [nT]             |
| `mag_1_igrf` | Vector{`T2`}    | Mag 1 IGRF & diurnal-corrected scalar magnetometer measurements [nT]      |
| `mag_1_uc`   | Vector{`T2`}    | Mag 1 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_2_uc`   | Vector{`T2`}    | Mag 2 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_3_uc`   | Vector{`T2`}    | Mag 3 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_4_uc`   | Vector{`T2`}    | Mag 4 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_5_uc`   | Vector{`T2`}    | Mag 5 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `mag_6_uc`   | Vector{`T2`}    | Mag 6 uncompensated (corrupted) scalar magnetometer measurements [nT]     |
| `ogs_mag`    | Vector{`T2`}    | OGS survey diurnal-corrected, levelled, magnetic field [nT]               |
| `ogs_alt`    | Vector{`T2`}    | OGS survey, GPS altitude (WGS-84) [m]                                     |
| `ins_wander` | Vector{`T2`}    | INS-computed wander angle (ccw from north) [rad]                          |
| `ins_roll`   | Vector{`T2`}    | INS-computed aircraft roll [deg]                                          |
| `ins_pitch`  | Vector{`T2`}    | INS-computed aircraft pitch [deg]                                         |
| `ins_yaw`    | Vector{`T2`}    | INS-computed aircraft yaw [deg]                                           |
| `roll_rate`  | Vector{`T2`}    | avionics-computed roll rate [deg/s]                                       |
| `pitch_rate` | Vector{`T2`}    | avionics-computed pitch rate [deg/s]                                      |
| `yaw_rate`   | Vector{`T2`}    | avionics-computed yaw rate [deg/s]                                        |
| `ins_acc_x`  | Vector{`T2`}    | INS x-acceleration [m/s^2]                                                |
| `ins_acc_y`  | Vector{`T2`}    | INS y-acceleration [m/s^2]                                                |
| `ins_acc_z`  | Vector{`T2`}    | INS z-acceleration [m/s^2]                                                |
| `lgtl_acc`   | Vector{`T2`}    | avionics-computed longitudinal (forward) acceleration [g]                 |
| `ltrl_acc`   | Vector{`T2`}    | avionics-computed lateral (starboard) acceleration [g]                    |
| `nrml_acc`   | Vector{`T2`}    | avionics-computed normal (vertical) acceleration [g]                      |
| `pitot_p`    | Vector{`T2`}    | avionics-computed pitot pressure [kPa]                                    |
| `static_p`   | Vector{`T2`}    | avionics-computed static pressure [kPa]                                   |
| `total_p`    | Vector{`T2`}    | avionics-computed total pressure [kPa]                                    |
| `cur_com_1`  | Vector{`T2`}    | current sensor: aircraft radio 1 [A]                                      |
| `cur_ac_hi`  | Vector{`T2`}    | current sensor: air conditioner fan high [A]                              |
| `cur_ac_lo`  | Vector{`T2`}    | current sensor: air conditioner fan low [A]                               |
| `cur_tank`   | Vector{`T2`}    | current sensor: cabin fuel pump [A]                                       |
| `cur_flap`   | Vector{`T2`}    | current sensor: flap motor [A]                                            |
| `cur_strb`   | Vector{`T2`}    | current sensor: strobe lights [A]                                         |
| `cur_srvo_o` | Vector{`T2`}    | current sensor: INS outer servo [A]                                       |
| `cur_srvo_m` | Vector{`T2`}    | current sensor: INS middle servo [A]                                      |
| `cur_srvo_i` | Vector{`T2`}    | current sensor: INS inner servo [A]                                       |
| `cur_heat`   | Vector{`T2`}    | current sensor: INS heater [A]                                            |
| `cur_acpwr`  | Vector{`T2`}    | current sensor: aircraft power [A]                                        |
| `cur_outpwr` | Vector{`T2`}    | current sensor: system output power [A]                                   |
| `cur_bat_1`  | Vector{`T2`}    | current sensor: battery 1 [A]                                             |
| `cur_bat_2`  | Vector{`T2`}    | current sensor: battery 2 [A]                                             |
| `vol_acpwr`  | Vector{`T2`}    | voltage sensor: aircraft power [V]                                        |
| `vol_outpwr` | Vector{`T2`}    | voltage sensor: system output power [V]                                   |
| `vol_bat_1`  | Vector{`T2`}    | voltage sensor: battery 1 [V]                                             |
| `vol_bat_2`  | Vector{`T2`}    | voltage sensor: battery 2 [V]                                             |
| `vol_res_p`  | Vector{`T2`}    | voltage sensor: resolver board (+) [V]                                    |
| `vol_res_n`  | Vector{`T2`}    | voltage sensor: resolver board (-) [V]                                    |
| `vol_back_p` | Vector{`T2`}    | voltage sensor: backplane (+) [V]                                         |
| `vol_back_n` | Vector{`T2`}    | voltage sensor: backplane (-) [V]                                         |
| `vol_gyro_1` | Vector{`T2`}    | voltage sensor: gyroscope 1 [V]                                           |
| `vol_gyro_2` | Vector{`T2`}    | voltage sensor: gyroscope 2 [V]                                           |
| `vol_acc_p`  | Vector{`T2`}    | voltage sensor: INS accelerometers (+) [V]                                |
| `vol_acc_n`  | Vector{`T2`}    | voltage sensor: INS accelerometers (-) [V]                                |
| `vol_block`  | Vector{`T2`}    | voltage sensor: block [V]                                                 |
| `vol_back`   | Vector{`T2`}    | voltage sensor: backplane [V]                                             |
| `vol_srvo`   | Vector{`T2`}    | voltage sensor: servos [V]                                                |
| `vol_cabt`   | Vector{`T2`}    | voltage sensor: cabinet [V]                                               |
| `vol_fan`    | Vector{`T2`}    | voltage sensor: cooling fan [V]                                           |
| `aux_1`      | Vector{`T2`}    | flexible-use auxiliary data 1                                             |
| `aux_2`      | Vector{`T2`}    | flexible-use auxiliary data 2                                             |
| `aux_3`      | Vector{`T2`}    | flexible-use auxiliary data 3                                             |
