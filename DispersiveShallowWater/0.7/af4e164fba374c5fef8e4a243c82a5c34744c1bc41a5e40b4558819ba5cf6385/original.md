```
momentum(q, equations)
```

Return the momentum/discharge of the primitive variables `q` for a given set of `equations`, i.e., the [`waterheight`](@ref) times the [`velocity`](@ref).

`q` is a vector of the primitive variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
