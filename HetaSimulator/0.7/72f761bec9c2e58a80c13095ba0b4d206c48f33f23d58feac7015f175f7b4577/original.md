```
fit(
  scenarios::AbstractVector{C},
  parameters_fitted;
  kwargs...
) where C<:AbstractScenario
```

Fit parameters to experimental measurements. Returns `FitResult` type.

Example:

`fit([scn2, scn3, scn4], [:k1=>0.1,:k2=>0.2,:k3=>0.3])`

Arguments:

  * `scenarios` : vector of scenarios of type [`Scenario`](@ref)
  * `parameters_fitted` : optimization parameters and their initial values
  * `kwargs...` : other ODE solver and `fit` related arguments supported by `fit(scenario_pairs::Vector{<:Pair}, parameters_fitted::Vector{<:Pair}`
