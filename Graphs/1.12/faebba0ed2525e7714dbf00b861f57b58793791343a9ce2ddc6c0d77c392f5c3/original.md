```
eccentricity(g[, v][, distmx])
eccentricity(g[, vs][, distmx])
```

Return the eccentricity[ies] of a vertex / vertex list `v` or a set of vertices `vs` defaulting to the entire graph. An optional matrix of edge distances may be supplied; if missing, edge distances default to `1`.

The eccentricity of a vertex is the maximum shortest-path distance between it and all other vertices in the graph.

The output is either a single float (when a single vertex is provided) or a vector of floats corresponding to the vertex vector. If no vertex vector is provided, the vector returned corresponds to each vertex in the graph.

### Performance

Because this function must calculate shortest paths for all vertices supplied in the argument list, it may take a long time.

### Implementation Notes

The eccentricity vector returned by `eccentricity()` may be used as input for the rest of the distance measures below. If an eccentricity vector is provided, it will be used. Otherwise, an eccentricity vector will be calculated for each call to the function. It may therefore be more efficient to calculate, store, and pass the eccentricities if multiple distance measures are desired.

An infinite path length is represented by the `typemax` of the distance matrix.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> eccentricity(g, 1)
2

julia> eccentricity(g, [1; 2])
2-element Vector{Int64}:
 2
 1

julia> eccentricity(g, [1; 2], [0 2 0; 0.5 0 0.5; 0 2 0])
2-element Vector{Float64}:
 2.5
 0.5
```
