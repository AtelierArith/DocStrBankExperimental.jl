```
waterheight(q, equations)
```

Return the waterheight of the primitive variables `q` for a given set of `equations`, i.e., the waterheight $h$ above the bathymetry $b$.

`q` is a vector of the primitive variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.

See also [`waterheight_total`](@ref), [`bathymetry`](@ref).
