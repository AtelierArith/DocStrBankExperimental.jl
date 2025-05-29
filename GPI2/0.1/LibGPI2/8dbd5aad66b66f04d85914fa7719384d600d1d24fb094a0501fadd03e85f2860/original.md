```
gaspi_atomic_fetch_add(segment_id, offset, rank, val_add, val_old, timeout_ms)
```

Atomic fetch-and-add

!!! warning
    The offset must be 8 bytes aligned.


### Parameters

  * `segment_id`: Segment identifier where data is located.
  * `offset`: Offset where data is located.
  * `rank`: The rank where to perform the operation.
  * `val_add`: The value to add.
  * `val_old`: Output parameter with the old value (before the add operation).
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_atomic_fetch_add (const gaspi_segment_id_t segment_id, const gaspi_offset_t offset, const gaspi_rank_t rank, const gaspi_atomic_value_t val_add, gaspi_atomic_value_t * const val_old, const gaspi_timeout_t timeout_ms);
```
