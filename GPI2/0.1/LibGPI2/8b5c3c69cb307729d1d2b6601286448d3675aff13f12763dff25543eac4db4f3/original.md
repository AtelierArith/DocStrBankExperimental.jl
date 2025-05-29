```
gaspi_queue_max(queue_max)
```

Get the maximum number of queues that may be used. It is the maximum of initialized queues plus dynamically created queues.

### Parameters

  * `queue_max`: Output parameter with maximum number of queues.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_queue_max(gaspi_number_t * const queue_max);
```
