```julia
struct CustomDenseHamiltonian{T<:Number, dimensionless_time, in_place} <: OpenQuantumBase.AbstractHamiltonian{T<:Number}
```

Defines a time dependent dense Hamiltonian object with custom function.

# Fields

  * `f`: Function for the Hamiltonian `H(s)`
  * `size`: Size
