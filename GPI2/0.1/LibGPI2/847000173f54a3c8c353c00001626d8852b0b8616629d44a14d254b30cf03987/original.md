```
gaspi_queue_size_max(queue_size_max)
```

Get the maximum number of elements that can be posted to a queue (outstanding requests).

### Parameters

  * `queue_size_max`: Output parameter with the maximum number of requests that can be posted to a queue.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_queue_size_max (gaspi_number_t * const queue_size_max);
```
