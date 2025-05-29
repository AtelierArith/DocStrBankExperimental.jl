```
ecdfplot(x::AbstractVector{<:Real}; kwargs...)
```

Plot the empirical cumulative distribution function (ECDF) of `x`. The `kwargs` may contain any option used in the `plot` module.

Example:     ecdfplot(randn(100), show=true)
