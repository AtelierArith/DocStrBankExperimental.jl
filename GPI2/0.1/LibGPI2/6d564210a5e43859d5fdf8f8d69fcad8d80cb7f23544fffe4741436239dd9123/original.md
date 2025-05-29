```
gaspi_disconnect(rank, timeout_ms)
```

Disconnect from a particular rank.

### Parameters

  * `rank`: Rank to disconnect from.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_disconnect (const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
