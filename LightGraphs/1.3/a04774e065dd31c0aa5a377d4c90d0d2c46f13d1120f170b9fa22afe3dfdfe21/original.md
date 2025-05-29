```
egonet(g, v, d, distmx=weights(g))
```

Return the subgraph of `g` induced by the neighbors of `v` up to distance `d`, using weights (optionally) provided by `distmx`. This is equivalent to [`induced_subgraph`](@ref)`(g, neighborhood(g, v, d, dir=dir))[1].`

### Optional Arguments

  * `dir=:out`: if `g` is directed, this argument specifies the edge direction

with respect to `v` (i.e. `:in` or `:out`).
