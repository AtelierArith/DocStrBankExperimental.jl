```
make_EnsembleProblem(metab_path, vect_init_cond, vect_params; tspan=(0.0, 1e8))
```

Create an `EnsembleProblem` for a metabolic pathway simulation with multiple initial conditions and parameters.

# Arguments

  * `metab_path::MetabolicPathway`: The metabolic pathway model to simulate.
  * `vect_init_cond::Vector{<:LArray}`: Vector of initial conditions for each ensemble member.
  * `vect_params::Vector{<:LArray}`: Vector of parameters for each ensemble member.
  * `tspan::Tuple{Float64,Float64}=(0.0, 1e8)`: Time span for the simulation.

# Returns

  * `EnsembleProblem`: An ensemble problem that can be solved using DifferentialEquations.jl's ensemble solvers.

# Notes

  * `vect_init_cond` and `vect_params` must have the same length.
  * Each element in the ensemble will use the corresponding initial conditions and parameters from the provided vectors.
  * The ensemble problem is constructed from a base ODE problem created with the first elements of the initial conditions and parameters vectors.

# Example

```julia
using CellMetabolismBase
using DifferentialEquations

metab_path = MetabolicPathway(...)
init_cond = LArray(...)
params = LArray(...)
tspan = (0.0, 1e8)
ensemble_prob = make_EnsembleProblem(metab_path, [init_cond1, init_cond2], [params1, params2], tspan)
ensemble_sol = solve(ensemble_prob, RadauIIA9(), trajectories=2)
```
