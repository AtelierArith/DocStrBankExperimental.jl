```julia
setup_mpi(settings)

```

Run this function once before running MPI jobs.  This should be done on the head node of a compute cluster. The setting are permanently saved.  See [`MPISettings`](@ref).
