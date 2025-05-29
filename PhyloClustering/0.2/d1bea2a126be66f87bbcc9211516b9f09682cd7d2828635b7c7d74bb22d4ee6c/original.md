```
get_bipartition(tree::HybridNetwork, n::Int64)
```

Get the bipartition format of a phylogenetic tree.

# Arguments

  * `tree`: a HybridNetwork object that reperents the tree.
  * `n`: the number of taxa of the tree.

# Output

A `Vector` of pairs shows the tree in bipartiton format.

# Example

```jldoctest
julia> get_bipartition(readTopology("(4:4.249,(1:2.457,(2:2.064,3:2.064):0.393):1.793);"), 4)
6-element Vector{Any}:
 3 => 4.249
 0 => 2.457
 1 => 2.064
 2 => 2.064
 6 => 0.393
 3 => 1.793
```
