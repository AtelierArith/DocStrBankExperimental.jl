```
k_core(g[, k]; corenum=core_number(g))
```

Return a vector of vertices in the k-core of graph `g`. If `k` is not specified, return the core with the largest degree.

A k-core is a maximal subgraph that contains vertices of degree `k` or more.

### Implementation Notes

Not implemented for graphs with self loops.

### References

  * An O(m) Algorithm for Cores Decomposition of Networks,   Vladimir Batagelj and Matjaz Zaversnik, 2003.   http://arxiv.org/abs/cs.DS/0310049

# Examples

```jldoctest
julia> using LightGraphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_core(g, 1)
5-element Array{Int64,1}:
 1
 2
 3
 4
 5

julia> k_core(g, 2)
4-element Array{Int64,1}:
 2
 3
 4
 5    
```
