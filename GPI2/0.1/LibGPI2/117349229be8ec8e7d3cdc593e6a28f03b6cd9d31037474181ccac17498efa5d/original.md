```
gaspi_proc_kill(rank, timeout_ms)
```

Kill a given process (rank).

### Parameters

  * `rank`: Rank to kill.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_proc_kill (const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
