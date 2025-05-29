```
gaspi_segment_alloc(segment_id, size, alloc_policy)
```

Allocate a segment.

### Parameters

  * `segment_id`: The segment identifier to be created.
  * `size`: The size of the segment to be created.
  * `alloc_policy`: The allocation policy.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_segment_alloc (const gaspi_segment_id_t segment_id, const gaspi_size_t size, const gaspi_alloc_t alloc_policy);
```
