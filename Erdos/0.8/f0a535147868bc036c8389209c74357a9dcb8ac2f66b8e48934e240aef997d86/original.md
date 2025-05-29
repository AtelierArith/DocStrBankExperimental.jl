```
periphery(g, distmx=weights(g))
periphery(all_ecc)
```

Returns the set of all vertices whose eccentricity is equal to the graph's diameter (that is, the set of vertices with the largest eccentricity).

Eventually a vector `all_ecc` contain the eccentricity of each node can be passed as argument.

See [`eccentricities`](@ref).
