```
gaspi_write_list(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

List of writes.

### Parameters

  * `num`: The number of list elements (see also [`gaspi_rw_list_elem_max`](@ref))
  * `segment_id_local`: List of local segments with data to be written.
  * `offset_local`: List of local offsets with data to be written.
  * `rank`: Rank to which will be written.
  * `segment_id_remote`: List of remote segments to write to.
  * `offset_remote`: List of remote offsets to write to.
  * `size`: List of sizes to write.
  * `queue`: The queue where to post the list.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_QUEUE_FULL if the requested could not be posted because the provided queue is full, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_write_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
