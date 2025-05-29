```
gaspi_segment_use(segment_id, pointer, size, group, timeout, memory_description)
```

Use a user-provided buffer as a segment.

### Parameters

  * `segment_id`: The segment identifier to be used.
  * `pointer`: The buffer address to use.
  * `size`: The size of segment.
  * `group`: The group participating in the operation.
  * `timeout`: The operation timeout (in milliseconds).
  * `memory_description`: A description of the memory to be used.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_segment_use (gaspi_segment_id_t const segment_id, gaspi_pointer_t const pointer, gaspi_size_t const size, gaspi_group_t const group, gaspi_timeout_t const timeout, gaspi_memory_description_t const memory_description);
```
