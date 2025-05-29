```
PiccoloOptions
```

Options for the Piccolo quantum optimal control library.

# Fields

  * `verbose::Bool = true`: Print verbose output
  * `timesteps_all_equal::Bool = true`: Use equal timesteps
  * `rollout_integrator::Function = expv`: Integrator to use for rollout
  * `geodesic = true`: Use the geodesic to initialize the optimization.
  * `zero_initial_and_final_derivative::Bool=false`: Zero the initial and final control pulse derivatives.
  * `complex_control_norm_constraint_name::Union{Nothing, Symbol} = nothing`: Name of the complex control norm constraint.
  * `complex_control_norm_constraint_radius::Float64 = 1.0`: Radius of the complex control norm constraint.
  * `bound_state::Bool = false`: Bound the state.
  * `leakage_suppression::Bool = false`: Suppress leakage.
  * `R_leakage::Float64 = 1.0`: Leakage suppression parameter.
