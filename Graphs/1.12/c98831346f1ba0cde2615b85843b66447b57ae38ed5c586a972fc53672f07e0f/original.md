```
k_crust(g[, k]; corenum=core_number(g))
```

Return a vector of vertices in the k-crust of `g`. If `k` is not specified, return the crust of the core with the largest degree.

The k-crust is the graph `g` with the [`k-core`](@ref k_core) removed.

### Implementation Notes

This definition of k-crust is different than the definition in References. The k-crust in References is equivalent to the `k+1` crust of this algorithm.

Not implemented for graphs with self loops.

### References

  * A model of Internet topology using k-shell decomposition  Shai Carmi, Shlomo Havlin, Scott Kirkpatrick, Yuval Shavitt,  and Eran Shir, PNAS  July 3, 2007   vol. 104  no. 27  11150-11154  http://www.pnas.org/content/104/27/11150.full

# Examples

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_crust(g, 0)
1-element Vector{Int64}:
 6

julia> k_crust(g, 1)
2-element Vector{Int64}:
 1
 6

julia> k_crust(g, 2)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
