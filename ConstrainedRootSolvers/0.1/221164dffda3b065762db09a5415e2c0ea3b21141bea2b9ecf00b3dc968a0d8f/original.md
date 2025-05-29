Newton's method constrained by mininum and maximum ranges for 1D root solver

```julia
mutable struct NewtonBisectionMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# Fields

  * `x_min::AbstractFloat`: Lower bound
  * `x_max::AbstractFloat`: Upper bound
  * `x_ini::AbstractFloat`: Initial guess
  * `history::Vector`: history of all simulations
