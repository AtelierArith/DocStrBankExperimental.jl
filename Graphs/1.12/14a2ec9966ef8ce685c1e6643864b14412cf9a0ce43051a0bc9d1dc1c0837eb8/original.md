```
k_corona(g, k; corenum=core_number(g))
```

Return a vector of vertices in the k-corona of `g`.

The k-corona is the subgraph of vertices in the [`k-core`](@ref k_core) which have exactly `k` neighbors in the k-core.

### Implementation Notes

Not implemented for graphs with parallel edges or self loops.

### References

  * k-core (bootstrap) percolation on complex networks:  Critical phenomena and nonlocal effects,  A. V. Goltsev, S. N. Dorogovtsev, and J. F. F. Mendes,  Phys. Rev. E 73, 056101 (2006)  http://link.aps.org/doi/10.1103/PhysRevE.73.056101

# Examples

```jldoctest
julia> using Graphs

julia> g = path_graph(5);

julia> add_vertex!(g);

julia> add_edge!(g, 5, 2);

julia> k_corona(g, 0)
1-element Vector{Int64}:
 6

julia> k_corona(g, 1)
1-element Vector{Int64}:
 1

julia> k_corona(g, 2)
4-element Vector{Int64}:
 2
 3
 4
 5

julia> k_corona(g, 3)
Int64[]
```
