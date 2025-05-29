```
waterheight(u, equations)
```

Return the water height associated to the conserved variables `u` for a given set of `equations`, e.g., the [`ShallowWaterEquations2D`](@ref).

`u` is a vector of the conserved variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
