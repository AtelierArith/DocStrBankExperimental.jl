```
fit(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::DataFrame;
  kwargs...
) where C<:AbstractScenario
```

Fit parameters to experimental measurements. Returns `FitResult` type.

Arguments:

  * `scenario_pairs` : vector of pairs containing names and scenarios of type [`Scenario`](@ref)
  * `parameters_fitted` : DataFrame with optimization parameters setup and their initial values, see [`read_parameters`](@ref)
  * `kwargs...` : other ODE solver and `fit` arguments supported by `fit(scenario_pairs::Vector{<:Pair}, parameters_fitted::Vector{<:Pair}`
