```
get_XYZ(flight::Symbol, df_flight::DataFrame;
        tt_sort::Bool      = true,
        reorient_vec::Bool = false,
        silent::Bool       = false)
```

Get `XYZ` flight data from saved HDF5 file via DataFrame lookup.

**Arguments:**

  * `flight`:    flight name (e.g., `:Flt1001`)
  * `df_flight`: lookup table (DataFrame) of flight data files

| **Field**  | **Type** | **Description**                                                                                               |
|:---------- |:-------- |:------------------------------------------------------------------------------------------------------------- |
| `flight`   | `Symbol` | flight name (e.g., `:Flt1001`)                                                                                |
| `xyz_type` | `Symbol` | subtype of `XYZ` to use for flight data {`:XYZ0`,`:XYZ1`,`:XYZ20`,`:XYZ21`}                                   |
| `xyz_set`  | `Real`   | flight dataset number (used to prevent improper mixing of datasets, such as different magnetometer locations) |
| `xyz_file` | `String` | path/name of flight data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)                 |

  * `tt_sort`:      (optional) if true, sort data by time (instead of line)
  * `reorient_vec`: (optional) if true, align vector magnetometer measurements with body frame
  * `silent`:       (optional) if true, no print outs

**Returns:**

  * `xyz`: `XYZ` flight data struct
