```
get_XYZ21(xyz_h5::String;
          info::String  = splitpath(xyz_h5)[end],
          tt_sort::Bool = true,
          silent::Bool  = false)
```

Get `XYZ21` flight data from saved HDF5 file. Based on 2021 SGL data fields.

**Arguments:**

  * `xyz_h5`:  path/name of flight data HDF5 file (`.h5` extension optional)
  * `info`:    (optional) flight data information
  * `tt_sort`: (optional) if true, sort data by time (instead of line)
  * `silent`:  (optional) if true, no print outs

**Returns:**

  * `xyz`: `XYZ21` flight data struct
