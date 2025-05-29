```julia
struct KPathInterpolant{D} <: Brillouin.KPaths.AbstractPath{StaticArraysCore.SArray{Tuple{D}, Float64, 1, D}}
```

  * `kpaths::Array{Array{StaticArraysCore.SVector{D, Float64}, 1}, 1} where D`
  * `labels::Vector{Dict{Int64, Symbol}}`
  * `basis::Bravais.ReciprocalBasis{D, Float64} where D`
  * `setting::Base.RefValue{Brillouin.BasisEnum}`
