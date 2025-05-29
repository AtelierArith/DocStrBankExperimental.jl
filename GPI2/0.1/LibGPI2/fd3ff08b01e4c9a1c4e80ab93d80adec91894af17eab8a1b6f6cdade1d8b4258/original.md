```
gaspi_queue_create(queue, timeout_ms)
```

Create a new communication queue.

### Parameters

  * `queue`: Output parameter with id of created queue.
  * `timeout_ms`: A timeout value in milliseconds.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_queue_create(gaspi_queue_id_t * const queue, const gaspi_timeout_t timeout_ms);
```
