```julia
struct PointGroup{D} <: Crystalline.AbstractGroup{D, Crystalline.SymOperation{D}}
```

  * `num::Int64`
  * `label::String`
  * `operations::Array{Crystalline.SymOperation{D}, 1} where D`
