```
mpiarray(T::DataType, Asize::Vararg{Int, N}; buffersize = 0, comm = MPI.COMM_WORLD, partition = (1, MPI.Comm_size(comm))) where {N}
```

construct a mpi array with size `Asize` and distributed on MPI `comm` with partition.
