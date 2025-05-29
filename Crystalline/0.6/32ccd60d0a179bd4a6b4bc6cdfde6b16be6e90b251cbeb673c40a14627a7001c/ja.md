```julia
struct LittleGroup{D} <: Crystalline.AbstractGroup{D, Crystalline.SymOperation{D}}
```

  * `num::Int64`
  * `kv::Crystalline.KVec`
  * `klab::String`
  * `operations::Array{Crystalline.SymOperation{D}, 1} where D`
