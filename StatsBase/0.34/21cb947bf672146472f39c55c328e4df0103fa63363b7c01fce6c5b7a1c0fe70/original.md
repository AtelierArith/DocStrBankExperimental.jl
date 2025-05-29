```
proportionmap(x)
proportionmap(x::AbstractVector, w::AbstractVector{<:Real})
```

Return a dictionary mapping each unique value in `x` to its proportion in `x`.

If a vector of weights `wv` is provided, the proportion of weights is computed rather than the proportion of raw counts.
