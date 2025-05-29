```
gaspi_threads_sync_all(g, timeout_ms)
```

Synchronize all threads in a group (global barrier). Implies a [`gaspi_barrier`](@ref) within the group.

### Parameters

  * `group`: The group involved in the barrier.
  * `timeout`: The timeout to be applied in the global barrier([`gaspi_barrier`](@ref)).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_threads_sync_all(const gaspi_group_t g, const gaspi_timeout_t timeout_ms) __attribute__ ((deprecated));
```
