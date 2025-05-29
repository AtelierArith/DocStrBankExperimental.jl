```
p4est_ghost_exchange_custom_levels_end(exc)
```

Complete an asynchronous ghost data exchange. This function waits for all pending MPI communications.

### Parameters

  * `Data`:[in,out] created ONLY by [`p4est_ghost_exchange_custom_levels_begin`](@ref). It is deallocated before this function returns.

### Prototype

```c
void p4est_ghost_exchange_custom_levels_end (p4est_ghost_exchange_t * exc);
```
