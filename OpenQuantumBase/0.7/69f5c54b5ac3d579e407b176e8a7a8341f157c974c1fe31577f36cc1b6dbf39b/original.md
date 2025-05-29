```julia
struct InterpSparseHamiltonian{T, dimensionless_time} <: OpenQuantumBase.AbstractHamiltonian{T}
```

Defines interpolating SparseHamiltonian object.

# Fields

  * `interp_obj`: Interpolating object
  * `size`: Size
