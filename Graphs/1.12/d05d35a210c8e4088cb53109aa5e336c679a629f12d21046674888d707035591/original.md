```
stress_centrality(g[, vs])
stress_centrality(g, k)
```

Calculate the [stress centrality](http://med.bioinf.mpi-inf.mpg.de/netanalyzer/help/2.7/#stressDist) of a graph `g` across all vertices, a specified subset of vertices `vs`, or a random subset of `k` vertices. Return a vector representing the centrality calculated for each node in `g`.

The stress centrality of a vertex $n$ is defined as the number of shortest paths passing through $n$.

### References

  * Barabási, A.L., Oltvai, Z.N.: Network biology: understanding the cell's functional organization. Nat Rev Genet 5 (2004) 101-113
  * Shimbel, A.: Structural parameters of communication networks. Bull Math Biophys 15 (1953) 501-507.

# Examples

```jldoctest
julia> using Graphs

julia> stress_centrality(star_graph(3))
3-element Vector{Int64}:
 2
 0
 0

julia> stress_centrality(cycle_graph(4))
4-element Vector{Int64}:
 2
 2
 2
 2
```
