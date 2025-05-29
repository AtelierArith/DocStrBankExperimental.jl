Bisection method for 1D root solvers

```julia
mutable struct BisectionMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# Fields

  * `x_min::AbstractFloat`: lower bound
  * `x_max::AbstractFloat`: upper bound
  * `xy::Matrix{FT} where FT<:AbstractFloat`: matrix that stores x and y, used in find_peak
  * `history::Vector`: history of all simulations
