```
gaspi_barrier(group, timeout_ms)
```

Barrier.

### Parameters

  * `group`: The group involved in the barrier.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_barrier (const gaspi_group_t group, const gaspi_timeout_t timeout_ms);
```
