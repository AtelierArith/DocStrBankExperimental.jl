```
get_XYZ20(xyz_160_h5::String, xyz_h5::String;
          info::String = splitpath(xyz_160_h5)[end] * " & " * splitpath(xyz_h5)[end],
          silent::Bool = false)
```

Get 160 Hz (partial) `XYZ20` flight data from saved HDF5 file and combine with 10 Hz `XYZ20` flight data from another saved HDF5 file. Data is time sorted to ensure data is aligned.

**Arguments:**

  * `xyz_160_h5`: path/name of 160 Hz flight data HDF5 file (`.h5` extension optional)
  * `xyz_h5`:     path/name of 10  Hz flight data HDF5 file (`.h5` extension optional)
  * `info`:       (optional) flight data information
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `xyz`: `XYZ20` flight data struct
