```
gaspi_atomic_compare_swap(segment_id, offset, rank, comparator, val_new, val_old, timeout_ms)
```

Atomic compare-and-swap.

### Parameters

  * `segment_id`: Segment identifier of data.
  * `offset`: Offset of data.
  * `rank`: The rank where to perform the operation.
  * `comparator`: The comparison value for the operation.
  * `val_new`: The new value to swap if comparison is successful.
  * `val_old`: Output parameter with the old value (before the operation).
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_atomic_compare_swap (const gaspi_segment_id_t segment_id, const gaspi_offset_t offset, const gaspi_rank_t rank, const gaspi_atomic_value_t comparator, const gaspi_atomic_value_t val_new, gaspi_atomic_value_t * const val_old, const gaspi_timeout_t timeout_ms);
```
