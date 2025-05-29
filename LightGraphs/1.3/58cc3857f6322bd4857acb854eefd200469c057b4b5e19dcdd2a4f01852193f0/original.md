```
clique_percolation(g, k=3)
```

Community detection using the clique percolation algorithm. Communities are potentionally overlapping. Return a vector of vectors `c` such that `c[i]` is the set of vertices in community `i`.  The parameter `k` defines the size of the clique to use in percolation.

### References

  * [Palla G, Derenyi I, Farkas I J, et al.](https://www.nature.com/articles/nature03607)

# Examples

```jldoctest
julia> using LightGraphs

julia> clique_percolation(clique_graph(3, 2))
2-element Array{BitSet,1}:
 BitSet([4, 5, 6])
 BitSet([1, 2, 3])

julia> clique_percolation(clique_graph(3, 2), k=2)
1-element Array{BitSet,1}:
 BitSet([1, 2, 3, 4, 5, 6])

julia> clique_percolation(clique_graph(3, 2), k=4)
0-element Array{BitSet,1}
```
