`Conductivity` is a data type to track electrical conductivity of a tight-binding model.

# Attributes

  * `M       ::  Model`: the tight-binding model whose conductivity is to be calculated.
  * `omegas  ::  Vector{Float64}`: The range of energies to integrate over to get the DC conductivity.
  * `spread  ::  Float64`: the disorder/spread in the real-frequency Greens function.
  * `spectral::  Vector{Array{Matrix{ComplexF64}}}`: the matrix Spectral function at the given frequencies, and all momentum points.
  * `sigma   ::  Dict{String, Float64}`: The dictionary containing the conductivity along the different directios.

Initialize this structure using 

```julia
Conductivity(M::Model ; spread::Float64 = 1e-3)
Conductivity(M::Model , omegas::Vector{Float64} ; spread::Float64 = 1e-3)
```

You can either input a filling, or a chemical potential. The corresponding μ for a given filling, or filling for a given μ is automatically calculated.
