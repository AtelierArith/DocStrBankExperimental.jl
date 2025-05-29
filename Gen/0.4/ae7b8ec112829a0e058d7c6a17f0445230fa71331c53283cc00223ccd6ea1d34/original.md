```
b::TraceTransformDSLProgram = inverse(a::TraceTransformDSLProgram)
```

Obtain the inverse of a bijection that was constructed with the [Trace Transform DSL](@ref).

The inverse must have been associated with the bijection either via [`pair_bijections!`](@ref) or [`is_involution!`])(@ref).
