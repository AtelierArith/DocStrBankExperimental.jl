```
center(g, distmx=weights(g))
center(all_ecc)
```

Returns the set of all vertices whose eccentricity is equal to the graph's radius (that is, the set of vertices with the smallest eccentricity).

Eventually a vector `all_ecc` contain the eccentricity of each node can be passed as argument.

See [`eccentricities`](@ref).
