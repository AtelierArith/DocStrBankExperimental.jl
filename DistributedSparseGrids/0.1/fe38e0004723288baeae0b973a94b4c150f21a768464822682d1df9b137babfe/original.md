```
init_weights_inplace_ops!(asg::SG, fun::F)
```

(Re-)Computes all weights in `asg` with in-place operations. In-place functions `mul!(::RT,::RT)`,`mul!(::RT,::Float64)`,`add!(::RT,::RT)` have to be defined.

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
