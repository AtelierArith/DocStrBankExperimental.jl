```
struct GMTfv{T<:AbstractFloat} <: AbstractMatrix{T}
```

The GMTfv struct is used to store a (mostly) triangulated mesh.

The fields of this struct are:

  * `verts::Matrix{T}`:         A Mx3 Matrix with the data vertices
  * `faces::Vector{<:Matrix{<:Int}}`:   A vector of matrices with the faces. Each row is a face
  * `faces_view::Vector{Matrix{Int}}`:  A subset of `faces` with only the visible faces from a certain perspective
  * `bbox::Vector{Float64}`:            The vertices BoundingBox
  * `color::Vector{Vector{String}}`:    A vector with G option colors for each face
  * `color_vwall::String`:              A string for makecpt cmap option argument (e.g. "darkgreen,lightgreen")
  * `zscale::Float64`:                  A multiplicative factor to scale the z values. Default is 1.
  * `bfculling::Bool`:                  If culling of invisible faces is wished. Default is true
  * `isflat::Vector{Bool}`:             If this is a flat mesh. Default is false
  * `proj4::String`:                    Projection string in PROJ4 syntax (Optional)
  * `wkt::String`:                      Projection string in WKT syntax (Optional)
  * `epsg::Int`:                        EPSG projection code (Optional)
