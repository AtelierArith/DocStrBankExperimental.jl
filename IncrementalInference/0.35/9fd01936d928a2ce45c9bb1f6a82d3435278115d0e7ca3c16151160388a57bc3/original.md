```julia
mutable struct CliqStateMachineContainer{BTND, G<:DistributedFactorGraphs.AbstractDFG, InMemG<:DistributedFactorGraphs.GraphsDFGs.GraphsDFG, BT<:IncrementalInference.AbstractBayesTree}
```

Container for upward tree solve / initialization.

DevNotes

  * TODO more direct clique access (cliq, parent, children), for multi-process solves
