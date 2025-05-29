```
distributed_init_weights_inplace_ops!(asg::SG, fun::F, worker_ids::Vector{Int})
```

(Re-)computes all weights in `asg` on all workers in `worker_ids`. In-place functions `mul!(::RT,::RT)`,`mul!(::RT,::Float64)`,`add!(::RT,::RT)` have to be defined.

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
  * `fun`::Function to be interpolated.
  * `worker_ids`: All available workers (can be added via `using Distributed; addprocs(...)`).
