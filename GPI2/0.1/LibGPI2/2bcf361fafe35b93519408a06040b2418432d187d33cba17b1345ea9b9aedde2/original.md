```
pgaspi_atomic_compare_swap(segment_id, offset, rank, comparator, val_new, val_old, timeout_ms)
```

### Prototype

```c
gaspi_return_t pgaspi_atomic_compare_swap (const gaspi_segment_id_t segment_id, const gaspi_offset_t offset, const gaspi_rank_t rank, const gaspi_atomic_value_t comparator, const gaspi_atomic_value_t val_new, gaspi_atomic_value_t * const val_old, const gaspi_timeout_t timeout_ms);
```
