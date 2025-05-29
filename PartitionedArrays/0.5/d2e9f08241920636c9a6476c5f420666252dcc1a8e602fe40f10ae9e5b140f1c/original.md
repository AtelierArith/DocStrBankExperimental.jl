```
distribute_with_mpi(a;comm::MPI.Comm=MPI.COMM_WORLD,duplicate_comm=true)
```

Create an [`MPIArray`](@ref) instance by distributing the items in the collection `a` over the ranks of the given MPI communicator `comm`. Each rank receives exactly one item, thus `length(a)`  and the communicator size need to match. For arrays that can store more than one item per rank see [`PVector`](@ref) or [`PSparseMatrix`](@ref). If `duplicate_comm=false` the result will take ownership of the given communicator. Otherwise, a copy will be done with `MPI.Comm_dup(comm)`.

!!! note
    This function calls `MPI.Init()` if MPI is not initialized yet.

