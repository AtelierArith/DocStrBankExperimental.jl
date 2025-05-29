Newton raphson method for 1D root solver

```julia
mutable struct NewtonRaphsonMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# Fields

  * `x_ini::AbstractFloat`: Initial guess
  * `history::Vector`: history of all simulations
