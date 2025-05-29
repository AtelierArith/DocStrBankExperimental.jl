```
gaspi_wait(queue, timeout_ms)
```

Wait for requests posted to a given queue.

### Parameters

  * `queue`: Queue to wait for.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_wait (const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
