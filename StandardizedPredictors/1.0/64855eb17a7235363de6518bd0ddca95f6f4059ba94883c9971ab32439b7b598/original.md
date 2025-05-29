```
scale(f=std, x, y=f(skipmissing(x)))
```

Scale an array `x` in place by a scalar `y`.

!!! warning
    This only scales and does not center the values, unlike `scale` in R. See `StatsBase.zscore` for that functionality.


See also [`scale`](@ref)
