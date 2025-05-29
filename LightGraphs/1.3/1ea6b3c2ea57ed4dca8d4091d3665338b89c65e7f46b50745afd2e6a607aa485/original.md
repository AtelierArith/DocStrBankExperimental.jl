```
k_shell(g[, k]; corenum=core_number(g))
```

Return a vector of vertices in the k-shell of `g`. If `k` is not specified, return the shell of the core with the largest degree.

The k-shell is the subgraph of vertices in the `k`-core but not in the (`k+1`)-core. This is similar to `k_corona` but in that case only neighbors in the k-core are considered.

### Implementation Notes

Not implemented for graphs with parallel edges or self loops.

### References

  * A model of Internet topology using k-shell decomposition  Shai Carmi, Shlomo Havlin, Scott Kirkpatrick, Yuval Shavitt,  and Eran Shir, PNAS  July 3, 2007   vol. 104  no. 27  11150-11154  http://www.pnas.org/content/104/27/11150.full

# Examples

```jldoctest
julia> using LightGraphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_shell(g, 0)
1-element Array{Int64,1}:
 6

julia> k_shell(g, 1)
1-element Array{Int64,1}:
 1

julia> k_shell(g, 2)
4-element Array{Int64,1}:
 2
 3
 4
 5
```
