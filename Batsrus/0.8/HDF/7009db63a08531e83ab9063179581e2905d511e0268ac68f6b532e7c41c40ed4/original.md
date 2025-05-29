```
 extract_var(file::BatsrusHDF5Uniform, var::String; kwargs...)
```

Extract variable `var` from HDF5 `file`.

# Keywords

  * `xmin`: minimum extracted coordinate in x.
  * `xmax`: maximum extracted coordinate in x.
  * `stepx`: extracted stride in x.
  * `ymin`: minimum extracted coordinate in y.
  * `ymax`: maximum extracted coordinate in y.
  * `stepy`: extracted stride in y.
  * `zmin`: minimum extracted coordinate in z.
  * `zmax`: maximum extracted coordinate in z.
  * `stepz`: extracted stride in z.
  * `verbose::Bool=true`: display type and size information of output variable.
