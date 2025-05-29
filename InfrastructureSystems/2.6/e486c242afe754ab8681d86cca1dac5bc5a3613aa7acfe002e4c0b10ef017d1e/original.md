```
mutable struct Deterministic <: AbstractDeterministic
    name::String
    data::SortedDict
    resolution::Dates.Period
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

A deterministic forecast for a particular data field in a Component.

# Arguments

  * `name::String`: user-defined name
  * `data::SortedDict`: timestamp - scalingfactor
  * `resolution::Dates.Period`: forecast resolution
  * `scaling_factor_multiplier::Union{Nothing, Function}`: Applicable when the time series data are scaling factors. Called on the associated component to convert the values.
  * `internal::InfrastructureSystemsInternal`
