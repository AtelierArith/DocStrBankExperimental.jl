```julia
struct MSpaceGroup{D} <: Crystalline.AbstractGroup{D, Crystalline.MSymOperation{D}}
```

  * `num::Tuple{Int64, Int64}`
  * `operations::Array{Crystalline.MSymOperation{D}, 1} where D`
