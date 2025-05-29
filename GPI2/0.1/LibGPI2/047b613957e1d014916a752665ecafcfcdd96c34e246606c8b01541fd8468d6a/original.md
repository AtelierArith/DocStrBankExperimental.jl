```
gaspi_segment_bind(segment_id, pointer, size, memory_description)
```

Use a user-provided buffer as a segment.

### Parameters

  * `segment_id`: The segment identifier to be used.
  * `pointer`: The buffer address to use.
  * `size`: The size of segment.
  * `memory_description`: A description of the memory to be used.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_segment_bind (gaspi_segment_id_t const segment_id, gaspi_pointer_t const pointer, gaspi_size_t const size, gaspi_memory_description_t const memory_description);
```
