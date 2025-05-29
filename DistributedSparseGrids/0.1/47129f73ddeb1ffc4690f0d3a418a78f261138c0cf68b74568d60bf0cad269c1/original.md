```
init_weights!(asg::SG, cpts::AbstractVector{HCP}, fun::F)
```

(Re-)Computes all weights in `cpts`. 

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
  * `cpts::AbstractVector{HCP}`: all weights of the collocation points in `cpts` will be (re-)calculated.
  * `fun`::Function to be interpolated.
