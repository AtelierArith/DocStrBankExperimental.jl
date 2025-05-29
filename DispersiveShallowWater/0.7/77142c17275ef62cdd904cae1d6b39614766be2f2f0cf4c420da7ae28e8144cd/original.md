```
waterheight_total(q, equations)
```

Return the total waterheight of the primitive variables `q` for a given set of `equations`, i.e., the [`waterheight`](@ref) $h$ plus the [`bathymetry`](@ref) $b$.

`q` is a vector of the primitive variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
