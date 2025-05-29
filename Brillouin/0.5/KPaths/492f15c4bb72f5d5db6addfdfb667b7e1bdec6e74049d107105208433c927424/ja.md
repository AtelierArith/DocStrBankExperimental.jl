```julia
struct KPath{D} <: Brillouin.KPaths.AbstractPath{Pair{Symbol, StaticArraysCore.SArray{Tuple{D}, Float64, 1, D}}}
```

  * `points::Dict{Symbol, StaticArraysCore.SVector{D, Float64}} where D`
  * `paths::Vector{Vector{Symbol}}`
  * `basis::Bravais.ReciprocalBasis{D, Float64} where D`
  * `setting::Base.RefValue{Brillouin.BasisEnum}`
