```
h5open(filename::AbstractString, mode::AbstractString="r"; swmr=false, pv...)
```

Open or create an HDF5 file where `mode` is one of:

  * "r"  read only
  * "r+" read and write
  * "cw" read and write, create file if not existing, do not truncate
  * "w"  read and write, create a new file (destroys any existing contents)

Pass `swmr=true` to enable (Single Writer Multiple Reader) SWMR write access for "w" and "r+", or SWMR read access for "r".

Properties can be specified as keywords for [`FileAccessProperties`](@ref) and [`FileCreateProperties`](@ref).

Also the keywords `fapl` and `fcpl` can be used to provide default instances of these property lists. Property lists passed in via keyword will be closed. This is useful to set properties not currently defined by HDF5.jl.

Note that `h5open` uses `fclose_degree = :strong` by default, but this can be overriden by the `fapl` keyword.
