```
distributed_init_weights!(asg::SG, fun::F, worker_ids::Vector{Int})
```

Computes all weights in `asg` on all workers in `worker_ids`. 

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: adaptive sparse grid
  * `fun`::Function to be interpolated.
  * `worker_ids`: All available workers (can be added via `using Distributed; addprocs(...)`).
