```
function estimator(
  scenarios::AbstractVector{C},
  parameters_fitted;
  kwargs...
) where {C<:AbstractScenario}
```

Generates likelihood estimator function for parameter identification and analysis.    It is the interface for scenarios in vector.   See more detailes in base `estimator` method.

Arguments:

  * `scenarios` : vector of scenarios of type [`Scenario`](@ref)
  * `parameters_fitted` : optimization parameters and their initial values
  * `kwargs...` : other arguments supported by `estimator`, see base method.
