```
init_weights!(asg::SG, fun::F)
```

(Re-)Computes all weights in `asg`. 

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
  * `fun`::Function to be interpolated.
