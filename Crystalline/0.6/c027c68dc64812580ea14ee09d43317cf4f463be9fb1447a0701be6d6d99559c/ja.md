```julia
struct SiteGroup{D} <: Crystalline.AbstractGroup{D, Crystalline.SymOperation{D}}
```

  * `num::Int64`
  * `wp::Crystalline.WyckoffPosition`
  * `operations::Array{Crystalline.SymOperation{D}, 1} where D`
  * `cosets::Array{Crystalline.SymOperation{D}, 1} where D`
