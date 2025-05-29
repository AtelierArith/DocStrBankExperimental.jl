```julia
struct DenseHamiltonian{T<:Number, dimensionless_time} <: OpenQuantumBase.AbstractDenseHamiltonian{T<:Number}
```

Defines a time dependent Hamiltonian object using Julia arrays.

# Fields

  * `f`: List of time dependent functions
  * `m`: List of constant matrices
  * `u_cache`: Internal cache
  * `size`: Size
