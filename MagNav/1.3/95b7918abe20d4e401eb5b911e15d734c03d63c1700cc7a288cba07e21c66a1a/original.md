```
get_ins(ins_file::String, field::Symbol = :ins_data;
        dt            = 0.1,
        tt_sort::Bool = true,
        silent::Bool  = false)
```

Get inertial navigation system data from saved CSV, HDF5, or MAT file. The only required fields are `ins_lat`, `ins_lon`, and `ins_alt` (position).

If a CSV or HDF5 file is provided, the possible columns/fields in the file are:

| **Field**   | **Type** | **Description**                                                                                                                 |
|:----------- |:-------- |:------------------------------------------------------------------------------------------------------------------------------- |
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

If a MAT file is provided, the above fields may also be provided, but they should be within the specified `field` MAT struct and without `ins_` prefixes. This is the standard way the MATLAB-companion outputs data.

**Arguments:**

  * `ins_file`: path/name of INS data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)
  * `field`:    (optional) struct field within MAT file to use, not relevant for CSV or HDF5 file
  * `dt`:       (optional) measurement time step [s], only used if not in `ins_file`
  * `silent`:   (optional) if true, no print outs

**Returns:**

  * `ins`: `INS` inertial navigation system struct
