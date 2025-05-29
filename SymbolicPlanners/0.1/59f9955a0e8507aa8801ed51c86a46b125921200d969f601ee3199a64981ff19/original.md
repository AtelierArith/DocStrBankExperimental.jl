```
planner = BidirectionalPlanner(;
    forward::ForwardPlanner = ForwardPlanner(),
    backward::BackwardPlanner = BackwardPlanner(),
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    save_search::Bool = false
)
```

A bi-directional planner which simulataneously runs a forward search from the initial state and backward search from the goal, succeeding if either search is successful, or if the search frontiers are detected to cross.

Frontier crossing is detected by checking whether the most recently expanded forward node is subsumed by a node in the backward search frontier, or vice versa. Subsumption means that the partial state represented by a backward node is consistent with the complete state represented by forward node.

While the above procedure is not complete (i.e. some crossings will be missed), it represents a trade-off between the cost of testing for subsumption and the  benefit of detecting a crossing, in lieu of more sophisticated methods [1].

[1] V. Alcázar, S. Fernández, and D. Borrajo, "Analyzing the Impact of Partial States on Duplicate Detection and Collision of Frontiers," ICAPS (2014), [https://doi.org/10.1609/icaps.v24i1.13677](https://doi.org/10.1609/icaps.v24i1.13677)

# Arguments

  * `forward`: Forward search configuration.
  * `backward`: Forward search configuration.
  * `max_nodes`: Maximum number of search nodes before termination.
  * `max_time`: Maximum time in seconds before planner times out.
  * `save_search`: Flag to save the search tree and frontier in the returned solution.
