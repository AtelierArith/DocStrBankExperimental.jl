```
gaspi_read_list(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

List of reads.

### Parameters

  * `num`: The number of list elements.
  * `segment_id_local`: List of local segments where data will be placed.
  * `offset_local`: List of local offsets where data will be placed.
  * `rank`: Rank from which will be read.
  * `segment_id_remote`: List of remote segments to read from.
  * `offset_remote`: List of remote offsets to read from.
  * `size`: List of sizes to read.
  * `queue`: The queue where to post the list.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_QUEUE_FULL if the requested could not be posted because the provided queue is full, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_read_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
