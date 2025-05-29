```
with_mpi(f;comm=MPI.COMM_WORLD,duplicate_comm=true)
```

Call `f(a->distribute_with_mpi(a;comm,duplicate_comm))` and abort MPI if there was an error.  This is the safest way of running the function `f` using MPI.

!!! note
    This function calls `MPI.Init()` if MPI is not initialized yet.

