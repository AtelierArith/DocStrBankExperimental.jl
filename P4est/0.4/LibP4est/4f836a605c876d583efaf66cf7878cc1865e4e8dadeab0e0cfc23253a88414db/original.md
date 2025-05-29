```
p8est_ghost_exchange_data_end(exc)
```

Complete an asynchronous ghost data exchange. This function waits for all pending MPI communications.

### Parameters

  * `exc`:[in,out] Created ONLY by [`p8est_ghost_exchange_data_begin`](@ref). It is deallocated before this function returns.

### Prototype

```c
void p8est_ghost_exchange_data_end (p8est_ghost_exchange_t * exc);
```
