```
gaspi_segment_ptr(segment_id, ptr)
```

Get the pointer to the location of a given segment.

### Parameters

  * `segment_id`: The segment identifier.
  * `ptr`: Output parameter with the pointer to the memory segment.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_segment_ptr (const gaspi_segment_id_t segment_id, gaspi_pointer_t * ptr);
```
