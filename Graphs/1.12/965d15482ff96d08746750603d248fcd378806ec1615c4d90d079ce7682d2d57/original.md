```
cycle_basis(g, root=nothing)
```

Return a list of cycles which form a basis for cycles of the undirected graph `g`, optionally starting at node `root`.

A basis for cycles of a network is a minimal collection of cycles such that any cycle in the network can be written as a sum of cycles in the basis.  Here summation of cycles is defined as "exclusive or" of the edges. Cycle bases are useful, e.g. when deriving equations for electric circuits using Kirchhoff's Laws.

# Examples

```jldoctest
julia> using Graphs

julia> elist = [(1,2),(2,3),(2,4),(3,4),(4,1),(1,5)];

julia> g = SimpleGraph(Graphs.SimpleEdge.(elist));

julia> cycle_basis(g)
2-element Vector{Vector{Int64}}:
 [2, 4, 1]
 [2, 3, 4]
```

### References

  * Paton, K. An algorithm for finding a fundamental set of cycles of a graph. Comm. ACM 12, 9 (Sept 1969), 514-518. [https://dl.acm.org/citation.cfm?id=363232]
