```julia
struct SubperiodicGroup{D, P} <: Crystalline.AbstractGroup{D, Crystalline.SymOperation{D}}
```

  * `num::Int64`
  * `operations::Array{Crystalline.SymOperation{D}, 1} where D`

A subperiodic group of embedding dimension `D` and periodicity dimension `P`. 

Fields: 

  * `operations`: the `SymOperation`s of the finite factor group $G/T$, where $G$ is the

subperiodic group and $T$ is the translation group of the associated lattice.

  * `num`: the canonical number of the group, following the International Tables for

Crystallography, Volume E.
