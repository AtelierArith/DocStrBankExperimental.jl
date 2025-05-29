```
get_flux(flux_file::String,
         use_vec::Symbol = :flux_a,
         field::Symbol   = :traj)
```

Get vector magnetometer data from saved CSV, HDF5, or MAT file.

If a CSV or HDF5 file is provided, the possible columns/fields in the file are:

| **Field**      | **Type** | **Description**                     |
|:-------------- |:-------- |:----------------------------------- |
| `use_vec`*`_x` | vector   | x-direction magnetic field [nT]     |
| `use_vec`*`_y` | vector   | y-direction magnetic field [nT]     |
| `use_vec`*`_z` | vector   | z-direction magnetic field [nT]     |
| `use_vec`*`_t` | vector   | total magnetic field [nT], optional |

If a MAT file is provided, the above fields may also be provided, but they should be within the specified `field` MAT struct. This is the standard way the MATLAB-companion outputs data.

**Arguments:**

  * `flux_file`: path/name of vector magnetometer data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)
  * `use_vec`:   (optional) vector magnetometer (fluxgate) to use
  * `field`:     (optional) struct field within MAT file to use, not relevant for CSV or HDF5 file

**Returns:**

  * `flux`: `MagV` vector magnetometer measurement struct
