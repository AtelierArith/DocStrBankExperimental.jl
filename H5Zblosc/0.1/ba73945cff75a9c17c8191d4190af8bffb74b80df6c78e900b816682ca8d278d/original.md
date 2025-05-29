```
BloscFilter(;level=5, shuffle=true, compressor="blosclz")
```

The Blosc compression filter, using [Blosc.jl](https://github.com/JuliaIO/Blosc.jl). Options:

  * `level`: compression level
  * `shuffle`: whether to shuffle data before compressing (this option should be used instead of the [`Shuffle`](@ref) filter)
  * `compressor`: the compression algorithm. Call `Blosc.compressors()` for the available compressors.

# External links

  * [What Is Blosc?](https://www.blosc.org/pages/blosc-in-depth/)
  * [Blosc HDF5 Filter ID 32001](https://portal.hdfgroup.org/display/support/Filters#Filters-32001)
  * [Blosc HDF5 Plugin Repository (C code)](https://github.com/Blosc/hdf5-blosc)
