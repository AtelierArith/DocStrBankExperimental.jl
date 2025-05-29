```
neighborhood(g, v, d, distmx=weights(g))
```

Return a vector of each vertex in `g` at a geodesic distance less than or equal to `d`, where distances may be specified by `distmx`.

### Optional Arguments

  * `dir=:out`: If `g` is directed, this argument specifies the edge direction

with respect to `v` of the edges to be considered. Possible values: `:in` or `:out`.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> neighborhood(g, 1, 2)
3-element Array{Int64,1}:
 1
 2
 3

julia> neighborhood(g, 1, 3)
4-element Array{Int64,1}:
 1
 2
 3
 4

julia> neighborhood(g, 1, 3, [0 1 0 0 0; 0 0 1 0 0; 1 0 0 0.25 0; 0 0 0 0 0.25; 0 0 0 0.25 0])
5-element Array{Int64,1}:
 1
 2
 3
 4
 5
```
