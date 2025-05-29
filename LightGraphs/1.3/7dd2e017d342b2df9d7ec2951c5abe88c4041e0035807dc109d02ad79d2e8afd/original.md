```
degree_centrality(g)
indegree_centrality(g)
outdegree_centrality(g)
```

Calculate the [degree centrality](https://en.wikipedia.org/wiki/Centrality#Degree_centrality) of graph `g`. Return a vector representing the centrality calculated for each node in `g`.

### Optional Arguments

  * `normalize=true`: If true, normalize each centrality measure by $\frac{1}{|V|-1}$.

# Examples

```jldoctest
julia> using LightGraphs

julia> degree_centrality(star_graph(4))
4-element Array{Float64,1}:
 1.0               
 0.3333333333333333
 0.3333333333333333
 0.3333333333333333

julia> degree_centrality(path_graph(3))
3-element Array{Float64,1}:
 0.5
 1.0
 0.5
```
