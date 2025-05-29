```
gaspi_proc_ping(rank, tout)
```

Ping a particular proc (rank). This is useful in FT applications to determine if a rank is alive.

### Parameters

  * `rank`: The rank to ping.
  * `tout`: A timeout value in milliseconds.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_proc_ping (const gaspi_rank_t rank, gaspi_timeout_t tout);
```
