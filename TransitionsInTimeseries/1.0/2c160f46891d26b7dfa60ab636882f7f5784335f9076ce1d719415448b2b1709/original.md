```
isequispaced(t; kwargs...) → true/false
```

Return `true` if time vector `t` is evenly spaced. For `AbstractRange` this is always true, while for `AbstractVector` successive differences in `t` are compared with `isapprox(; kwargs...)` and if all are approximately the same then `true` is returned.
