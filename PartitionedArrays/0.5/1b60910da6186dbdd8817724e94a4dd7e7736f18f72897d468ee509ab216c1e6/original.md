```
struct OwnAndGhostVectors{A,C,T}
```

Vector type that stores the local values of a [`PVector`](@ref) instance using a vector of own values, a vector of ghost values, and a permutation.

# Properties

  * `own_values::A`: The vector of own values.
  * `ghost_values::A`: The vector of ghost values.
  * `permumation::C`: A permutation vector such that `vcat(own_values,ghost_values)[permutation]` corresponds to the local values.

# Supertype hierarchy

```
OwnAndGhostVectors{A,C,T} <: AbstractVector{T}
```
