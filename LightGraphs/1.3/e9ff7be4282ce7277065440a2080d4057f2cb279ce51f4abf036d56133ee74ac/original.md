```
transitiveclosure!(g, selflooped=false)
```

Compute the transitive closure of a directed graph, using DFS. If `selflooped` is true, add self loops to the graph.

### Performance

Time complexity is $\mathcal{O}(|E||V|)$.

### Implementation Notes

This version of the function modifies the original graph.
