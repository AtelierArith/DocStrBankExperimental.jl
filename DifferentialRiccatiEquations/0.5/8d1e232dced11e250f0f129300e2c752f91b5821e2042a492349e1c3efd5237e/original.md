```
lowrank(L, D)::LDLᵀ
```

A lazy representation of `alpha * L * D * L'` where `alpha::Real` is initially one, that supports the following functions:

  * `+(::LDLᵀ, ::LDLᵀ)`
  * `*(::Real, ::LDLᵀ)`
  * `eltype(::LDLᵀ)` which yields `Base.promote_eltype(L, D)` (same as `typeof(alpha)`)
  * `size`
  * `rank` which yields the length of the inner dimension, i.e. `size(L, 2)`
  * `zero` which yields a rank 0 representation
  * [`concatenate!`](@ref) (expert use only)
  * [`compress!`](@ref) (expert use only)

Iterating the structure yields `alpha`, `L` and `D`. This calls [`compress!`](@ref), if necessary.

For convenience, the structure might be converted to a matrix via `Matrix`. It is recommended to use this only for testing.
