```
eval_equation(model::AbstractModel, eqn::AbstractEquation, sim_data::AbstractMatrix{Float64}, rng::UnitRange{Int64} = 1:size(sim_data,1))
```

Evaluate the residuals of a given equation over a range of time points.

This function calculates the residuals of the provided equation `eqn` for each time step in the range `rng` from the simulated data `sim_data`. The model's lag and lead structure is respected during evaluation.

# Arguments

  * `model::AbstractModel`: The model containing the equation to be evaluated.
  * `eqn::AbstractEquation`: The equation for which residuals are to be calculated.
  * `sim_data::AbstractMatrix{Float64}`: The simulated data, with rows representing time points and columns representing model.allvars (variables, shocks and auxiliary variables).
  * `rng::UnitRange{Int64}`: The range of time points over which to evaluate the equation. By default, evaluates over all time points in `sim_data`.

# Returns

  * `res::Vector{Float64}`: A vector of residuals for each time point in the range `rng`. Entries for time points where residuals cannot be computed (due to insufficient lags or leads) are filled with `NaN`.
