```
greedy_treewidth_deletion(G::LabeledGraph, m::Int=4;
                          score_function::Symbol=:tree_trimming, 
                          elim_order::Array{Symbol, 1}=[])
```

Greedily remove vertices from G with respect to minimising the chosen score function. Return the reduced graph and an array of vertices which were removed.

The intermediate elimination orders and corresponding treewidths of the intermediate graphs are also returned if an elimination order for G is provided.

The algorithm is described by Schutski et al in Phys. Rev. A 102, 062614.

# Keywords

  * `score_function::Symbol=:tree_trimming`: function to maximise when selecting vertices to remove.                                          (:degree, :direct*treewidth, :tree*trimming)
  * `elim_order::Array{Symbol, 1}=Symbol[]`: The elimination order for G to be used by                                           direct_treewidth score function.
