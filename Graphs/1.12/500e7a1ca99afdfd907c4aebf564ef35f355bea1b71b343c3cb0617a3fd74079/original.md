```
modularity(g, c, distmx=weights(g), γ=1.0)
```

Return a value representing Newman's modularity `Q` for the undirected and  directed graph `g` given the partitioning vector `c`. This method also supports weighted graphs if the distance matrix is provided.

Modularity $Q$ for undirected graph:

$$
Q = \frac{1}{2m} \sum_{c} \left( e_{c} - \gamma \frac{K_c^2}{2m} \right)
$$

Modularity $Q$ for directed graph:

$$
Q = \frac{1}{m} \sum_{c} \left( e_{c} - \gamma \frac{K_c^{in} K_c^{out}}{m} \right)
$$

where:

  * $m$: total number of edges in the network
  * $e_c$: number of edges in community $c$
  * $K_c$: sum of the degrees of the nodes in community $c$ or the  sum of the weighted degree of the nodes in community $c$ when the graph is  weighted. $K_c^{in}$ sum of the in-degrees of the nodes in community $c$.

### Optional Arguments

  * `distmx=weights(g)`: distance matrix for weighted graphs
  * `γ=1.0`: where `γ > 0` is a resolution parameter. When the modularity is used  to find communities structure in networks (i.e with [Louvain's method for  community detection](https://en.wikipedia.org/wiki/Louvain_Modularity)),  higher resolutions lead to more communities, while lower resolutions lead to  fewer communities. Where `γ=1.0` it lead to the traditional definition of  the modularity.

### References

  * M. E. J. Newman and M. Girvan. "Finding and evaluating community structure in networks".  Phys. Rev. E 69, 026113 (2004). [(arXiv)](https://arxiv.org/abs/cond-mat/0308217)
  * J. Reichardt and S. Bornholdt. "Statistical mechanics of community detection".  Phys. Rev. E 74, 016110 (2006). [(arXiv)](https://arxiv.org/abs/cond-mat/0603718)
  * E. A. Leicht and M. E. J. Newman. "Community structure in directed networks".  Physical Review Letter, 100:118703, (2008). [(arXiv)](https://arxiv.org/pdf/0709.4500.pdf)

# Examples

```jldoctest
julia> using Graphs

julia> barbell = blockdiag(complete_graph(3), complete_graph(3));

julia> add_edge!(barbell, 1, 4);

julia> modularity(barbell, [1, 1, 1, 2, 2, 2])
0.35714285714285715

julia> modularity(barbell, [1, 1, 1, 2, 2, 2], γ=0.5)
0.6071428571428571  
```

```jldoctest
julia> using Graphs

julia> triangle = cycle_graph(3);

julia> barbell = blockdiag(triangle, triangle);

julia> add_edge!(barbell, 1, 4);

julia> distmx = Matrix(weights(barbell));

julia> distmx[1, 4] = distmx[4, 1] = 5;  # additional edge has a weight of 5

julia> round(modularity(barbell, [1, 1, 1, 2, 2, 2]; distmx), digits=6)
0.045455
```
