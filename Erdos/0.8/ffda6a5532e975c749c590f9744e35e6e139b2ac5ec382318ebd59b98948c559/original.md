```
eccentricities(g, distmx=weights(g))
eccentricities(g, vs, distmx=weights(g))
```

Returns `[eccentricity(g,v,distmx) for v in vs]`. When `vs` it is not supplied, considers all node in the graph.

See also [`eccentricity`](@ref).

Note: the eccentricity vector returned by `eccentricity` may be eventually used as input in some eccentricity related measures ([`periphery`](@ref), [`center`](@ref)).
