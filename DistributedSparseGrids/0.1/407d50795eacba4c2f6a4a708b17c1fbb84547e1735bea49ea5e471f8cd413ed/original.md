```
init_weights_inplace_ops!(asg::SG, cpts::AbstractVector{HCP}, fun::F)
```

(Re-)Computes all weights in `cpts` with in-place operations. In-place functions `mul!(::RT,::RT)`,`mul!(::RT,::Float64)`,`add!(::RT,::RT)` have to be defined.

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
  * `cpts::AbstractVector{HCP}`: all weights of the collocation points in `cpts` will be (re-)calculated.
  * `fun`::Function to be interpolated.
