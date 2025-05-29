Reduce step method for 1D root solver. This method increases or decreases from     initial guess until no improvement is found. Then the incremantal step     decreases, and then the root solver continues.

```julia
mutable struct ReduceStepMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# Fields

  * `x_min::AbstractFloat`: Lower bound
  * `x_max::AbstractFloat`: Upper bound
  * `x_ini::AbstractFloat`: Initial guess
  * `Δ_ini::AbstractFloat`: Initial step
  * `history::Vector`: history of all simulations
