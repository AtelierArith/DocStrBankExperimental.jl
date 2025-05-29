```
gather!(A, A_global)
gather!(A, A_global; root=0)
```

!!! note "Advanced"
    ```
    gather!(A, A_global, comm; root=0)
    ```


Gather an array `A` from each member of the Cartesian grid of MPI processes into one large array `A_global` on the root process (default: `0`). The size of the global array `size(A_global)` must be equal to the product of `size(A)` and `dims`, where `dims` is the number of processes in each dimension of the Cartesian grid, defined in [`init_global_grid`](@ref).

!!! note "Advanced"
    If the argument `comm` is given, then this communicator is used for the gather operation and `dims` extracted from it.


!!! note "Memory requirements"
    The memory for the global array only needs to be allocated on the root process; the argument `A_global` can be `nothing` on the other processes.

