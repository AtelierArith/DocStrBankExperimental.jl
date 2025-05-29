```
closeness_centrality(g, distmx=weights(g); normalize=true)
```

Calculate the [closeness centrality](https://en.wikipedia.org/wiki/Centrality#Closeness_centrality) of the graph `g`. Return a vector representing the centrality calculated for each node in `g`.

### Optional Arguments

  * `normalize=true`: If true, normalize the centrality value of each

node `n` by $\frac{|δ_n|}{|V|-1}$, where $δ_n$ is the set of vertices reachable from node `n`.

# Examples

```jldoctest
julia> using Graphs

julia> closeness_centrality(star_graph(5))
5-element Vector{Float64}:
 1.0
 0.5714285714285714
 0.5714285714285714
 0.5714285714285714
 0.5714285714285714

julia> closeness_centrality(path_graph(4))
4-element Vector{Float64}:
 0.5
 0.75
 0.75
 0.5
```
