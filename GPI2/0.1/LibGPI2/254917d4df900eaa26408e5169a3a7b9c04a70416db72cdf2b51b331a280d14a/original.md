```
gaspi_segment_create(segment_id, size, group, timeout_ms, alloc_policy)
```

Create a segment. It is semantically equivalent to a collective aggregation of gaspi_segment_ alloc, [`gaspi_segment_register`](@ref) and [`gaspi_barrier`](@ref) involving all of the mem- bers of a given group.

### Parameters

  * `segment_id`: The segment id to identify the segment.
  * `size`: The size of the segment (in bytes).
  * `group`: The group of ranks with which the segment should be registered.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).
  * `alloc_policy`: Memory allocation policy.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_segment_create (const gaspi_segment_id_t segment_id, const gaspi_size_t size, const gaspi_group_t group, const gaspi_timeout_t timeout_ms, const gaspi_alloc_t alloc_policy);
```
