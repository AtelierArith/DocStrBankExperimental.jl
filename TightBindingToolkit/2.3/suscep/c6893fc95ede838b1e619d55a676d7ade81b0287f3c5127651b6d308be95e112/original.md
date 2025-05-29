`Susceptibility` is a data type representing the magnetic response, $χ^{ab}(Q , Ω)$ for a general tight-binding `Model`.

# Attributes

  * `M       ::  Model`: the given model.
  * `Qs      ::  Vector{Vector{Float64}}`: the set of momentum points over which $χ^{ab}(Q , Ω)$ is calculated.
  * `Omegas  ::  Vector{Float64}`: the set of energies over which $χ^{ab}(Q , Ω)$ is calculated.
  * `Spread  ::  Float64` : the finite spread when summing over delta functions.
  * `chis    ::  Dict`: a dictionary containing $χ^{ab}(Q , Ω)$ for the different directions e.g. `chis["xx"]` etc.

Initialize this structure using 

```julia
Susceptibility(M::Model , Omegas::Vector{Float64} ;  eta::Float64 = 1e-2) = new{}(M, [], Omegas, eta, Dict())
Susceptibility(M::Model , Qs::Vector{Vector{Float64}}, Omegas::Vector{Float64} ;  eta::Float64 = 1e-2) = new{}(M, Qs, Omegas, eta, Dict())
```
