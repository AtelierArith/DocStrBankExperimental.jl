```
incidencemat(rn::ReactionSystem; sparse=false)
```

Calculate the incidence matrix of `rn`, see [`reactioncomplexes`](@ref).

Notes:

  * Is cached in `rn` so that future calls, assuming the same sparsity, will also be fast.
