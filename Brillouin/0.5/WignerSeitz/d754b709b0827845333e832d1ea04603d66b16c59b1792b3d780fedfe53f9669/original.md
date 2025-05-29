```julia
struct Cell{D} <: AbstractArray{Array{StaticArraysCore.SArray{Tuple{D}, Float64, 1, D}, 1}, 1}
```

  * `verts::Array{StaticArraysCore.SVector{D, Float64}, 1} where D`
  * `faces::Vector{Vector{Int64}}`
  * `basis::StaticArraysCore.SArray{Tuple{D}, StaticArraysCore.SVector{D, Float64}, 1, D} where D`
  * `setting::Base.RefValue{Brillouin.BasisEnum}`
