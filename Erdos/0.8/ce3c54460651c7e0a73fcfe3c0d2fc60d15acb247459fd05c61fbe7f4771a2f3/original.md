```
egonet(g, v::Int, d::Int; dir=:out)
```

Returns the subgraph of `g` induced by the neighbors of `v` up to distance `d`. If `g` is a `DiGraph` the `dir` optional argument specifies the edge direction the edge direction with respect to `v` (i.e. `:in` or `:out`) to be considered. This is equivalent to [`subgraph`](@ref)`(g, neighborhood(g, v, d, dir=dir))[1].`
