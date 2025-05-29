```julia
struct AdiabaticFrameHamiltonian{T} <: OpenQuantumBase.AbstractDenseHamiltonian{T}
```

Defines a time dependent Hamiltonian in adiabatic frame.

# Fields

  * `geometric`: Geometric part
  * `diagonal`: Adiabatic part
  * `size`: Size of the Hamiltonian
