```
core_number(g)
```

Return the core number for each vertex in graph `g`.

A k-core is a maximal subgraph that contains vertices of degree `k` or more. The core number of a vertex is the largest value `k` of a k-core containing that vertex.

### Implementation Notes

Not implemented for graphs with self loops.

### References

  * An O(m) Algorithm for Cores Decomposition of Networks,   Vladimir Batagelj and Matjaz Zaversnik, 2003.   http://arxiv.org/abs/cs.DS/0310049

# Examples

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> core_number(g)
6-element Vector{Int64}:
 1
 2
 2
 2
 2
 0
```
