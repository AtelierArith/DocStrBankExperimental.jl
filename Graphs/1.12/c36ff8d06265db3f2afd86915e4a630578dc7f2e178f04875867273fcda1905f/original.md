```
betweenness_centrality(g[, vs])
betweenness_centrality(g, k)
```

Calculate the [betweenness centrality](https://en.wikipedia.org/wiki/Centrality#Betweenness_centrality) of a graph `g` across all vertices, a specified subset of vertices `vs`, or a random subset of `k` vertices. Return a vector representing the centrality calculated for each node in `g`.

### Optional Arguments

  * `normalize=true`: If true, normalize the betweenness values by the

total number of possible distinct paths between all pairs in the graphs. For an undirected graph, this number is $\frac{(|V|-1)(|V|-2)}{2}$ and for a directed graph, ${(|V|-1)(|V|-2)}$.

  * `endpoints=false`: If true, include endpoints in the shortest path count.

Betweenness centrality is defined as: $bc(v) = \frac{1}{\mathcal{N}} \sum_{s \neq t \neq v} \frac{\sigma_{st}(v)}{\sigma_{st}}$.

### References

  * Brandes 2001 & Brandes 2008

# Examples

```jldoctest
julia> using Graphs

julia> betweenness_centrality(star_graph(3))
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> betweenness_centrality(path_graph(4))
4-element Vector{Float64}:
 0.0
 0.6666666666666666
 0.6666666666666666
 0.0
```
