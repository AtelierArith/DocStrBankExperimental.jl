```
function estimator(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::DataFrame;
  kwargs...
) where C<:AbstractScenario
```

Generates likelihood estimator function for parameter identification and analysis.    It is the interface for parameters from `DataFrame`.   See more detailes in base `estimator` method.

Arguments:

  * `scenario_pairs` : vector of pairs containing names and scenarios of type [`Scenario`](@ref)
  * `parameters_fitted` : DataFrame with optimization parameters setup and their initial values, see [`read_parameters`](@ref)
  * `kwargs...` : other arguments supported by `estimator`, see base method.
