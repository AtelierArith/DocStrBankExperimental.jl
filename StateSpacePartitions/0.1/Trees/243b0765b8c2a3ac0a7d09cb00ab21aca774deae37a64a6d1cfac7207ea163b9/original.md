```
determine_partition(trajectory, tree_type::Tree{Val{false}, S}; override = false) where S
```

# Decription

This function determines the partition of a trajectory into an unstructured tree. The tree structure is specified by the `tree_type` argument. The `trajectory` argument is a trajectory of states. The `override` keyword argument is a boolean indicating whether to override the truncation of the trajectory.

# Arguments

  * `trajectory`: a trajectory of states
  * `tree_type`: a `Tree` type

# Keyword Arguments

  * `override`: a boolean indicating whether to override the truncation of the trajectory

# Returns

  * `embedding`: a `Tree` object
