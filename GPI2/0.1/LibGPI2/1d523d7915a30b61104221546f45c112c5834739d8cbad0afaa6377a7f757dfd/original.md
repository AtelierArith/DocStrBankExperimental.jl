```
gaspi_read(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

One-sided read.

### Parameters

  * `segment_id_local`: The local segment id where data will be placed.
  * `offset_local`: The local offset where the data will be placed.
  * `rank`: The rank from which we want to read.
  * `segment_id_remote`: The remote segment id to read from.
  * `offset_remote`: The remote offset where to read from.
  * `size`: The size of data to read.
  * `queue`: The queue where to post the read request.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_QUEUE_FULL if the requested could not be posted because the provided queue is full, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_read (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
