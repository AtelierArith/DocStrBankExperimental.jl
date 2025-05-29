```
Constant(value)
```

A constant function compatible with interval arithmetic.

Return an interval containing only the value for an interval input, and the value directly otherwise.

```jldoctest
julia> c = Constant(1.2)
Constant{Float64}(1.2)

julia> c(22.2)
1.2

julia> c(interval(0, 1.3))
Interval{Float64}(1.2, 1.2, com)
```

Note that this is not equivalent to `Returns(value)` from base, which always outputs `value`, even for an interval input. This can shortcircuit the propagation of intervals in the computation and lose the associated guarantee of correctness.
