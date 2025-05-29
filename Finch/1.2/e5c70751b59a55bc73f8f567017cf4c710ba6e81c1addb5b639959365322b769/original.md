```
bspwrite(::AbstractString, tns)
bspwrite(::HDF5.File, tns)
bspwrite(::NPYPath, tns)
```

Write the Finch tensor to a file using [Binsparse](https://github.com/GraphBLAS/binsparse-specification) file format.

Supported file extensions are:

  * `.bsp.h5`: HDF5 file format ([HDF5](https://github.com/JuliaIO/HDF5.jl) must be loaded)
  * `.bspnpy`: NumPy and JSON directory format ([NPZ](https://github.com/fhs/NPZ.jl) must be loaded)

!!! warning
    The Binsparse spec is under development. Additionally, this function may not be fully conformant. Please file bug reports if you see anything amiss.

