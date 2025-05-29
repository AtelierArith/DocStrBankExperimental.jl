```
betweenness_centrality(g; normalize=true, endpoints=false, approx=-1)
```

Calculates the [betweenness centrality](https://en.wikipedia.org/wiki/Centrality#Betweenness_centrality) of the vertices of graph `g`.

Betweenness centrality for vertex `v` is defined as:

$$
bc(v) = \frac{1}{\mathcal{N}} \sum_{s \neq t \neq v}
        \frac{\sigma_{st}(v)}{\sigma_{st}},
$$

where $\sigma _{st}} \sigma_{st}$ is the total number of shortest paths from node `s` to node `t` and $\sigma_{st}(v)$ is the number of those paths that pass through `v`.

If `endpoints=true`, endpoints are included in the shortest path count.

If `normalize=true`, the betweenness values are normalized by the total number of possible distinct paths between all pairs in the graph. For an undirected graph, this number if `((n-1)*(n-2))/2` and for a directed graph, `(n-1)*(n-2)` where `n` is the number of vertices in the graph.

If  an integer argument `approx > 0` is given, returns an approximation of the betweenness centrality of each vertex of the graph involving `approx` randomly chosen vertices.

**References**

[1] Brandes 2001 & Brandes 2008
