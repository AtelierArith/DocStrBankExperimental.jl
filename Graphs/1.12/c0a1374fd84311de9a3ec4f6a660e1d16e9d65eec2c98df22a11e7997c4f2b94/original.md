```
radiality_centrality(g)
```

Calculate the [radiality centrality](http://www.cbmc.it/fastcent/doc/Radiality.htm) of a graph `g` across all vertices. Return a vector representing the centrality calculated for each node in `g`.

The radiality centrality $R_u$ of a vertex $u$ is defined as $R_u = \frac{D_g + 1 - \frac{\sum_{v∈V}d_{u,v}}{|V|-1}}{D_g}$

where $D_g$ is the diameter of the graph and $d_{u,v}$ is the  length of the shortest path from $u$ to $v$.

### References

  * Brandes, U.: A faster algorithm for betweenness centrality. J Math Sociol 25 (2001) 163-177

# Examples

```jldoctest
julia> using Graphs

julia> radiality_centrality(star_graph(4))
4-element Vector{Float64}:
 1.0               
 0.6666666666666666
 0.6666666666666666
 0.6666666666666666

julia> radiality_centrality(path_graph(3))
3-element Vector{Float64}:
 0.75
 1.0 
 0.75
```
