```
sc_is_root()
```

Identify the root process. Only meaningful between [`sc_init`](@ref) and [`sc_finalize`](@ref) and with a communicator that is not `sc_MPI_COMM_NULL` (otherwise always true).

### Returns

Return true for the root process and false otherwise.

### Prototype

```c
int sc_is_root (void);
```
