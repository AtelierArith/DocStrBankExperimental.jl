```
KnotPointObjective(
    ℓ::Function,
    names::AbstractVector{Symbol},
    traj::NamedTrajectory,
    params::AbstractVector;
    kwargs...
)
KnotPointObjective(
    ℓ::Function,
    names::AbstractVector{Symbol},
    traj::NamedTrajectory;
    kwargs...
)
KnotPointObjective(
    ℓ::Function,
    name::Symbol,
    args...;
    kwargs...
)
```

Create a knot point summed objective function for trajectory optimization, where `ℓ(x, p)`  on trajectory knot point variables `x` with parameters `p`. If the parameters argument is  omitted, `ℓ(x)` is assumed  to be a function of `x` only.

# Arguments

  * `ℓ::Function`: Function that defines the objective, ℓ(x, p) or ℓ(x).
  * `names::AbstractVector{Symbol}`: Names of the trajectory variables to be optimized.
  * `traj::NamedTrajectory`: The trajectory on which the objective is defined.
  * `params::AbstractVector`: Parameters `p` for the objective function ℓ, for each time.

# Keyword Arguments

  * `times::AbstractVector{Int}=1:traj.T`: Time indices at which the objective is evaluated.
  * `Qs::AbstractVector{Float64}=ones(traj.T)`: Weights for the objective function at each time.
