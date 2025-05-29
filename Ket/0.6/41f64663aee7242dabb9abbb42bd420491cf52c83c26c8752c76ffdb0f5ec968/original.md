```
tensor_correlation(p::AbstractArray, behaviour::Bool = false; collinsgisin::Bool = false, marg::Bool = true)
```

Converts a multipartite Bell functional `p` into correlation notation. If `collinsgisin` is `true`, `p` is assumed to be written in Collins-Gisin notation. Otherwise, `p` is assumed to be written in probability notation. If `marg` is `false`, the output contains only full correlators, with no marginals. If `behaviour` is `true` do the transformation for behaviours. Doesn't assume normalization.

Also accepts the arguments of `tensor_probability` (state and measurements) for convenience.
