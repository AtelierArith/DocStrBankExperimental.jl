```
get_XYZ1(xyz_file::String,
         traj_field::Symbol = :traj,
         ins_field::Symbol  = :ins_data;
         info::String       = splitpath(xyz_file)[end],
         flight             = 1,
         line               = 1,
         year               = 2023,
         doy                = 154,
         dt                 = 0.1,
         tt_sort::Bool      = true,
         silent::Bool       = false)
```

Get the minimum dataset required for MagNav from saved CSV, HDF5, or MAT file. Not all fields within the `XYZ1` flight data struct are required. The minimum data required in the CSV, HDF5, or MAT file includes:

  * `lat`, `lon`, `alt` (position)
  * `mag_1_c` OR `mag_1_uc` (scalar magnetometer measurements)

All other fields can be computed/simulated, except `flux_b`, `mag_2_c`, `mag_3_c`, `mag_2_uc`, `mag_3_uc`, `aux_1`, `aux_2`, and `aux_3`.

If a CSV or HDF5 file is provided, the possible columns/fields in the file are:

| **Field**   | **Type** | **Description**                                                                                                                 |
|:----------- |:-------- |:------------------------------------------------------------------------------------------------------------------------------- |
| `dt`        | scalar   | measurement time step [s]                                                                                                       |
| `tt`        | vector   | time [s]                                                                                                                        |
| `lat`       | vector   | latitude  [deg]                                                                                                                 |
| `lon`       | vector   | longitude [deg]                                                                                                                 |
| `alt`       | vector   | altitude  [m]                                                                                                                   |
| `vn`        | vector   | north velocity [m/s]                                                                                                            |
| `ve`        | vector   | east  velocity [m/s]                                                                                                            |
| `vd`        | vector   | down  velocity [m/s]                                                                                                            |
| `fn`        | vector   | north specific force [m/s]                                                                                                      |
| `fe`        | vector   | east  specific force [m/s]                                                                                                      |
| `fd`        | vector   | down  specific force [m/s]                                                                                                      |
| `Cnb`       | 3x3xN    | direction cosine matrix (body to navigation) [-], not valid for CSV file (use `roll`, `pitch`, & `yaw` instead)                 |
| `roll`      | vector   | roll [deg]                                                                                                                      |
| `pitch`     | vector   | pitch [deg]                                                                                                                     |
| `yaw`       | vector   | yaw [deg]                                                                                                                       |
| `ins_dt`    | scalar   | INS measurement time step [s]                                                                                                   |
| `ins_tt`    | vector   | INS time [s]                                                                                                                    |
| `ins_lat`   | vector   | INS latitude  [deg]                                                                                                             |
| `ins_lon`   | vector   | INS longitude [deg]                                                                                                             |
| `ins_alt`   | vector   | INS altitude  [m]                                                                                                               |
| `ins_vn`    | vector   | INS north velocity [m/s]                                                                                                        |
| `ins_ve`    | vector   | INS east  velocity [m/s]                                                                                                        |
| `ins_vd`    | vector   | INS down  velocity [m/s]                                                                                                        |
| `ins_fn`    | vector   | INS north specific force [m/s]                                                                                                  |
| `ins_fe`    | vector   | INS east  specific force [m/s]                                                                                                  |
| `ins_fd`    | vector   | INS down  specific force [m/s]                                                                                                  |
| `ins_Cnb`   | 3x3xN    | INS direction cosine matrix (body to navigation) [-], not valid for CSV file (use `ins_roll`, `ins_pitch`, & `ins_yaw` instead) |
| `ins_roll`  | vector   | INS roll [deg]                                                                                                                  |
| `ins_pitch` | vector   | INS pitch [deg]                                                                                                                 |
| `ins_yaw`   | vector   | INS yaw [deg]                                                                                                                   |
| `ins_P`     | 17x17xN  | INS covariance matrix, only relevant for simulated data, otherwise zeros [-], not valid for CSV file                            |
| `flux_a_x`  | vector   | Flux A x-direction magnetic field [nT]                                                                                          |
| `flux_a_y`  | vector   | Flux A y-direction magnetic field [nT]                                                                                          |
| `flux_a_z`  | vector   | Flux A z-direction magnetic field [nT]                                                                                          |
| `flux_a_t`  | vector   | Flux A total magnetic field [nT]                                                                                                |
| `flux_b_x`  | vector   | Flux B x-direction magnetic field [nT]                                                                                          |
| `flux_b_y`  | vector   | Flux B y-direction magnetic field [nT]                                                                                          |
| `flux_b_z`  | vector   | Flux B z-direction magnetic field [nT]                                                                                          |
| `flux_b_t`  | vector   | Flux B total magnetic field [nT]                                                                                                |
| `flight`    | vector   | flight number(s)                                                                                                                |
| `line`      | vector   | line number(s), i.e., segments within `flight`                                                                                  |
| `year`      | vector   | year                                                                                                                            |
| `doy`       | vector   | day of year                                                                                                                     |
| `diurnal`   | vector   | measured diurnal, i.e., temporal variations or space weather effects [nT]                                                       |
| `igrf`      | vector   | International Geomagnetic Reference Field (IGRF), i.e., core field [nT]                                                         |
| `mag_1_c`   | vector   | Mag 1 compensated (clean) scalar magnetometer measurements [nT]                                                                 |
| `mag_2_c`   | vector   | Mag 2 compensated (clean) scalar magnetometer measurements [nT]                                                                 |
| `mag_3_c`   | vector   | Mag 3 compensated (clean) scalar magnetometer measurements [nT]                                                                 |
| `mag_1_uc`  | vector   | Mag 1 uncompensated (corrupted) scalar magnetometer measurements [nT]                                                           |
| `mag_2_uc`  | vector   | Mag 2 uncompensated (corrupted) scalar magnetometer measurements [nT]                                                           |
| `mag_3_uc`  | vector   | Mag 3 uncompensated (corrupted) scalar magnetometer measurements [nT]                                                           |
| `aux_1`     | vector   | flexible-use auxiliary data 1                                                                                                   |
| `aux_2`     | vector   | flexible-use auxiliary data 2                                                                                                   |
| `aux_3`     | vector   | flexible-use auxiliary data 3                                                                                                   |

If a MAT file is provided, the above fields may also be provided, but the non-INS fields should be within the specified `traj_field` MAT struct and the INS fields should be within the specified `ins_field` MAT struct and without `ins_` prefixes. This is the standard way the MATLAB-companion outputs data.

**Arguments:**

  * `xyz_file`:   path/name of flight data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)
  * `traj_field`: (optional) trajectory struct field within MAT file to use, not relevant for CSV or HDF5 file
  * `ins_field`:  (optional) INS struct field within MAT file to use, `:none` if unavailable, not relevant for CSV or HDF5 file
  * `tt_sort`:    (optional) if true, sort data by time (instead of line)
  * `silent`:     (optional) if true, no print outs

If not provided in `xyz_file`:

  * `info`:   (optional) flight data information
  * `flight`: (optional) flight number
  * `line`:   (optional) line number, i.e., segment within `flight`
  * `year`:   (optional) year
  * `doy`:    (optional) day of year
  * `dt`:     (optional) measurement time step [s]

**Returns:**

  * `xyz`: `XYZ1` flight data struct
