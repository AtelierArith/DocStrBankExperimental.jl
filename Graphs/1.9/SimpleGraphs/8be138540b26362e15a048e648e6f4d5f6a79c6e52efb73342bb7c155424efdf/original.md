```
rem_vertex!(g, v)
```

Remove the vertex `v` from graph `g`. Return `false` if removal fails (e.g., if vertex is not in the graph); `true` otherwise.

### Performance

Time complexity is $\mathcal{O}(k^2)$, where $k$ is the max of the degrees of vertex $v$ and vertex $|V|$.

### Implementation Notes

This operation has to be performed carefully if one keeps external data structures indexed by edges or vertices in the graph, since internally the removal is performed swapping the vertices `v`  and $|V|$, and removing the last vertex $|V|$ from the graph. After removal the vertices in `g` will be indexed by $1:|V|-1$.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> rem_vertex!(g, 2)
true

julia> rem_vertex!(g, 2)
false
```
