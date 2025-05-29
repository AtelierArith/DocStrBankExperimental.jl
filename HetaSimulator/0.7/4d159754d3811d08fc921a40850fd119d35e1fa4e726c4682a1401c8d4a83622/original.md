```
fit(platform::Platform,
  parameters_fitted;
  scenarios::Union{AbstractVector{Symbol}, Nothing} = nothing,
  kwargs...
) where C<:AbstractScenario
```

Fit parameters to experimental measurements. Returns `FitResult` type.

Example:

`fit(platform, [:k1=>0.1,:k2=>0.2,:k3=>0.3];scenarios=[:scn2,:scn3])`

Arguments:

  * `platform` : platform of [`Platform`](@ref) type
  * `parameters_fitted` : optimization parameters and their initial values
  * `scenarios` : vector of scenarios identifiers of type `Symbol`. Default is `nothing`
  * `kwargs...` : other ODE solver and `fit` related arguments supported by `fit(scenario_pairs::Vector{<:Pair}, parameters_fitted::Vector{<:Pair}`
