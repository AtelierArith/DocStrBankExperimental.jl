```
NCCLBackend(comm = nothing, mpi_backend = nothing)
```

Create an NCCL backend for distributed training. Users should not use this function directly. Instead use [`DistributedUtils.get_distributed_backend(NCCLBackend)`](@ref).
