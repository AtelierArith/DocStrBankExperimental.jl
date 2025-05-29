bspread(::AbstractString) bspread(::HDF5.File) bspread(::NPYPath)

Read the [Binsparse](https://github.com/GraphBLAS/binsparse-specification) file into a Finch tensor.

Supported file extensions are:

  * `.bsp.h5`: HDF5 file format ([HDF5](https://github.com/JuliaIO/HDF5.jl) must be loaded)
  * `.bspnpy`: NumPy and JSON directory format ([NPZ](https://github.com/fhs/NPZ.jl) must be loaded)

!!! warning



The Binsparse spec is under development. Additionally, this function may not be fully conformant. Please file bug reports if you see anything amiss.
