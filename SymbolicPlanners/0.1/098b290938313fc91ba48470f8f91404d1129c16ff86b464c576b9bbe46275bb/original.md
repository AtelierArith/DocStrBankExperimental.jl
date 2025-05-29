```
BiPathSearchSolution(status, plan)
BiPathSearchSolution(status, plan, trajectory)
BiPathSearchSolution(status, plan, trajectory, expanded,
                     f_search_tree, f_frontier, f_expanded, f_trajectory,
                     b_search_tree, b_frontier, b_expanded, b_trajectory)
```

Solution type for bidirectional search-based planners.

# Fields

  * `status`: Status of the returned solution.
  * `plan`: Sequence of actions that reach the goal. May be partial / incomplete.
  * `trajectory`: Trajectory of states that will be traversed while following the plan.
  * `expanded`: Number of nodes expanded during search.
  * `f_search_tree`: Forward search tree.
  * `f_frontier`: Forward search frontier.
  * `f_expanded`: Number of nodes expanded via forward search.
  * `f_trajectory`: Trajectory of states returned by forward search.
  * `b_search_tree`: Backward search tree.
  * `b_frontier`: Backward search frontier.
  * `b_expanded`: Number of nodes expanded via backward search.
  * `b_trajectory`: Trajectory of states returned by backward search.
