```
readSTL(filename::String; verbose::Bool=false, tol::Float64=eps(Float64), zeroBased::Bool=false)
```

Read STL file to obtain geometry. This function can also handle the non-standard Tagged Multi Solid file type that OpenVSP writes out. Connectivity information for the mesh is not available at present.

**Arguments**

  * `filename::String`: STL filename
  * `verbose::Bool`: Set to `true` to print status messages during file read operation
  * `tol::Float64`: Set absolute tolerance when comparing points to obtain connectivity
  * `zeroBased::Bool`: Set true to use [zero-based numbering](https://en.wikipedia.org/wiki/Zero-based_numbering) for indices in connectivity information

**Returns**

  * `geom`: Vector of `GeometryBasics.Mesh` objects from the ['Geometrybasics.jl'](https://juliageometry.github.io/GeometryBasics.jl/stable/) package
