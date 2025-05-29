```
determine_partition(trajectory, tree_type::Tree{Val{true}, S}; override = false) where S
```

# Decription

This function determines the partitioning of the state space into a binary tree. The tree is determined by recursively splitting the state space into two parts. The splitting is done by k-means clustering. The number of levels of the tree is determined by the `levels` keyword argument. If the trajectory is too long, it is truncated to roughly 1000 points per level. The `override` keyword argument can be used to override this behavior.

# Arguments

  * `trajectory`: a trajectory of states
  * `tree_type`: a `Tree` type

# Keyword Arguments

  * `override`: a boolean indicating whether to override the truncation of the trajectory

# Returns

  * `embedding`: a `Tree` object
