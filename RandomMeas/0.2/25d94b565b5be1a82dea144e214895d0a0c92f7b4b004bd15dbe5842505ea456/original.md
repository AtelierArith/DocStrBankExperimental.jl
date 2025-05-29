```
get_trace_product(shadows::AbstractShadow...; O::Union{Nothing, MPO}=nothing)
```

Compute the product of multiple shadow objects and return its trace or expectation value.

If `O` is `nothing`, returns the trace of the product:     trace(shadow₁ * shadow₂ * ... * shadowₙ). If `O` is provided, returns the expectation value computed by:     get*expect*shadow(O, shadow₁ * shadow₂ * ... * shadowₙ).

# Arguments

  * `shadows...`: A variable number of shadow objects.
  * `O::Union{Nothing, MPO}` (optional): An MPO observable.

# Returns

The trace of the product if `O` is `nothing`, or the expectation value if `O` is provided.

# Example

```julia
result = get_trace_product(shadow1, shadow2, shadow3)
result_with_O = get_trace_product(shadow1, shadow2, shadow3; O=my_operator)
```
