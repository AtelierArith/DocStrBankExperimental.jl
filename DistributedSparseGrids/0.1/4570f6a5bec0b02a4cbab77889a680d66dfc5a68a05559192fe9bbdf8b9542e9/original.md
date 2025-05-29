```
distributed_init_weights_inplace_ops!(asg::SG, cpts::AbstractVector{HCP}, fun::F, worker_ids::Vector{Int})
```

Computes all weights in `cpts` on all workers in `worker_ids`. In-place functions `mul!(::RT,::RT)`,`mul!(::RT,::Float64)`,`add!(::RT,::RT)` have to be defined.

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
  * `cpts::AbstractVector{HCP}`: all weights of the collocation points in `cpts` will be (re-)calculated.
  * `fun`::Function to be interpolated.
  * `worker_ids`: All available workers (can be added via `using Distributed; addprocs(...)`).
