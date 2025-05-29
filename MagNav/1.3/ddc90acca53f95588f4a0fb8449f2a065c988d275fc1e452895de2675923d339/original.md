```
get_traj(traj_file::String, field::Symbol = :traj;
         dt            = 0.1,
         tt_sort::Bool = true,
         silent::Bool  = false)
```

Get trajectory data from saved CSV, HDF5, or MAT file. The only required fields are `lat`, `lon`, and `alt` (position).

If a CSV or HDF5 file is provided, the possible columns/fields in the file are:

| **Field** | **Type** | **Description**                                                                                                 |
|:--------- |:-------- |:--------------------------------------------------------------------------------------------------------------- |
| `dt`      | scalar   | measurement time step [s]                                                                                       |
| `tt`      | vector   | time [s]                                                                                                        |
| `lat`     | vector   | latitude  [deg]                                                                                                 |
| `lon`     | vector   | longitude [deg]                                                                                                 |
| `alt`     | vector   | altitude  [m]                                                                                                   |
| `vn`      | vector   | north velocity [m/s]                                                                                            |
| `ve`      | vector   | east  velocity [m/s]                                                                                            |
| `vd`      | vector   | down  velocity [m/s]                                                                                            |
| `fn`      | vector   | north specific force [m/s]                                                                                      |
| `fe`      | vector   | east  specific force [m/s]                                                                                      |
| `fd`      | vector   | down  specific force [m/s]                                                                                      |
| `Cnb`     | 3x3xN    | direction cosine matrix (body to navigation) [-], not valid for CSV file (use `roll`, `pitch`, & `yaw` instead) |
| `roll`    | vector   | roll [deg]                                                                                                      |
| `pitch`   | vector   | pitch [deg]                                                                                                     |
| `yaw`     | vector   | yaw [deg]                                                                                                       |

If a MAT file is provided, the above fields may also be provided, but they should be within the specified `field` MAT struct. This is the standard way the MATLAB-companion outputs data.

**Arguments:**

  * `traj_file`: path/name of trajectory data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)
  * `field`:     (optional) struct field within MAT file to use, not relevant for CSV or HDF5 file
  * `dt`:        (optional) measurement time step [s], only used if not in `traj_file`
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `traj`: `Traj` trajectory struct
