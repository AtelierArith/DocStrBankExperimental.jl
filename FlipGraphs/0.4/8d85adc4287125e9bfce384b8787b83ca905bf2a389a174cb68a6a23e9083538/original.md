```
flipgraph_planar(n::Integer; modular=false) :: FlipGraphPlanar
```

Construct the `FlipGraphPlanar` of a convex `n`-gon. 

If `modular=true`, the flip graph is reduced to its modular form.

# Examples

```julia-repl
julia> flipgraph_planar(6)
FlipGraphPlanar with 14 vertices and 21 edges
```
