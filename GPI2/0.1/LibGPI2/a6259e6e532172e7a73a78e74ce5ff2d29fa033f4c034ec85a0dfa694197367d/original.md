```
gaspi_queue_size(queue, queue_size)
```

Get the current number of elements on a given queue.

### Parameters

  * `queue`: The queue to get the size.
  * `queue_size`: Output parameter with the size/elements in the queue.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_queue_size (const gaspi_queue_id_t queue, gaspi_number_t * const queue_size);
```
