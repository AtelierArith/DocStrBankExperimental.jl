```
evaluate(model, data...; cache=true, options...)
```

Equivalent to `evaluate!(machine(model, data..., cache=cache); options...)`. See the machine version `evaluate!` for the complete list of options.

Returns a  [`PerformanceEvaluation`](@ref) object.

See also [`evaluate!`](@ref).
