```julia
struct SparseHamiltonian{T<:Number, dimensionless_time} <: OpenQuantumBase.AbstractHamiltonian{T<:Number}
```

Defines a time dependent Hamiltonian object with sparse matrices.

# Fields

  * `f`: List of time dependent functions
  * `m`: List of constant matrices
  * `u_cache`: Internal cache
  * `size`: Size
