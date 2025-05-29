```
entropy(q, equations)
```

Return the entropy of the primitive variables `q` for a given set of `equations`. For all [`AbstractShallowWaterEquations`](@ref), the `entropy` is just the [`energy_total`](@ref).

`q` is a vector of the primitive variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
