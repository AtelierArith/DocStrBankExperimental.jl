```
position!(LA::ForceDirectedLayout, L::Dict{K,NodePosition}, N::T) where {T <: EcologicalNetworks.AbstractEcologicalNetwork} where {K}
```

One iteration of the force-directed layout routine. Because these algorithms can take some time to converge, it may be useful to stop every 500 iterations to have a look at the results. Note that to avoid oscillations, the maximum displacement at any given time is set to 0.01 units.

These layouts tend to have O(N³) complexity, where N is the number of nodes in the network. This is because repulsion required to do (N×(N-1))/2 visits on pairs of nodes, and an optimal layout usually requires s×N steps to converge. With the maximal displacement set to 0.01, we have found that k ≈ 100 gives acceptable results. This will depend on the complexity of the network, and its connectance, as well as the degree and edge strengths distributions.
