```julia
struct SpaceGroup{D} <: Crystalline.AbstractGroup{D, Crystalline.SymOperation{D}}
```

  * `num::Int64`
  * `operations::Array{Crystalline.SymOperation{D}, 1} where D`
