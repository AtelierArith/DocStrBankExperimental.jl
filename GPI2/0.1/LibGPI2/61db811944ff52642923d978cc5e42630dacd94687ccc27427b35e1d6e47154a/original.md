```
pgaspi_read_list(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

### Prototype

```c
gaspi_return_t pgaspi_read_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
