```julia
struct InterpDenseHamiltonian{T, isdimensionlesstime} <: OpenQuantumBase.AbstractDenseHamiltonian{T}
```

Defines interpolating DenseHamiltonian object.

# Fields

  * `interp_obj`: Interpolating object
  * `size`: Size
