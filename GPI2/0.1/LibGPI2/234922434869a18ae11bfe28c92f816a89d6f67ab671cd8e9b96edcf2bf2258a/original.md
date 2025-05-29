```
pgaspi_queue_purge(queue, timeout_ms)
```

Purge queue.

### Parameters

  * `queue`: The queue to purge.
  * `timeout_ms`: Timeout for operation.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error or GASPI_TIMEOUT in case time has expired.

### Prototype

```c
gaspi_return_t pgaspi_queue_purge(const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
