```
function estimator(
  platform::Platform,
  parameters_fitted;
  scenarios::Union{AbstractVector{Symbol}, Nothing} = nothing, # all if nothing
  kwargs... 
)
```

Generates likelihood estimator function for parameter identification and analysis.    It is the interface for Platform.   See more detailes in base `estimator` method.

Arguments:

  * `platform` : platform of [`Platform`](@ref) type
  * `parameters_fitted` : optimization parameters and their initial values
  * `scenarios` : vector of scenarios identifiers of type `Symbol`. Default is `nothing`
  * `kwargs...` : other arguments supported by `estimator`, see base method.
