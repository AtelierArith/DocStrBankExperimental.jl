```
transitiveclosure(g, selflooped=false)
```

Compute the transitive closure of a directed graph, using DFS. Return a graph representing the transitive closure. If `selflooped` is `true`, add self loops to the graph.

### Performance

Time complexity is $\mathcal{O}(|E||V|)$.

# Examples

```jldoctest
julia> using Graphs

julia> barbell = blockdiag(complete_digraph(3), complete_digraph(3));

julia> add_edge!(barbell, 1, 4);

julia> ne(barbell)
13

julia> ne(transitiveclosure(barbell))
21
```
