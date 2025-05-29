```
gaspi_connect(rank, timeout_ms)
```

Connect to a determined rank to be able to communicate. It builds the required infrastructure for communication.

### Parameters

  * `rank`: Rank to connect to.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_connect (const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
