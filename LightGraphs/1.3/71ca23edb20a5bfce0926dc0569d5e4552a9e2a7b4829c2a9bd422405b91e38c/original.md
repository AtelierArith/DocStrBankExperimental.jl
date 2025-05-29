```
neighborhood_dists(g, v, d, distmx=weights(g))
```

Return a a vector of tuples representing each vertex which is at a geodesic distance less than or equal to `d`, along with its distance from `v`. Non-negative distances may be specified by `distmx`.

### Optional Arguments

  * `dir=:out`: If `g` is directed, this argument specifies the edge direction

with respect to `v` of the edges to be considered. Possible values: `:in` or `:out`.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> neighborhood_dists(g, 1, 3)
4-element Array{Tuple{Int64,Int64},1}:
 (1, 0)
 (2, 1)
 (3, 2)
 (4, 3)

julia> neighborhood_dists(g, 1, 3, [0 1 0 0 0; 0 0 1 0 0; 1 0 0 0.25 0; 0 0 0 0 0.25; 0 0 0 0.25 0])
5-element Array{Tuple{Int64,Float64},1}:
 (1, 0.0)
 (2, 1.0)
 (3, 2.0)
 (4, 2.25)
 (5, 2.5)

julia> neighborhood_dists(g, 4, 3)
2-element Array{Tuple{Int64,Int64},1}:
 (4, 0)
 (5, 1)

julia> neighborhood_dists(g, 4, 3, dir=:in)
5-element Array{Tuple{Int64,Int64},1}:
 (4, 0)
 (3, 1)
 (5, 1)
 (2, 2)
 (1, 3)
```
