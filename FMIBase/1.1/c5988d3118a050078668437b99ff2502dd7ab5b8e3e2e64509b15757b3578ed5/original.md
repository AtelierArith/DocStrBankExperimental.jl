```
FMUInputFunction(inputFunction, vrs)
```

Struct container for inplace input functions for FMUs.

# Arguments

  * `inputFunction`: The input function (inplace) that gets called when new inputs are needed, must match one of the patterns described under *Input function patterns*.
  * `vrs::AbstractVector`: A vector of value refernces to be set by the input function

## Input function patterns

Available input patterns are [`c`: current component, `u`: current state ,`t`: current time, returning array of values to be passed to `fmi2SetReal(..., inputValueReferences, inputFunction(...))` or `fmi3SetFloat64`]:

  * `inputFunction(t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, u::AbstractVector{<:Real})`
  * `inputFunction(x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
