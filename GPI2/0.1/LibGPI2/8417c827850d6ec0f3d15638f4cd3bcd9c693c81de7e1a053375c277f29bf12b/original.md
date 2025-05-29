```
gaspi_write(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

One-sided write.

### Parameters

  * `segment_id_local`: The local segment id with the data to write.
  * `offset_local`: The local offset with the data to write.
  * `rank`: The rank to which we want to write.
  * `segment_id_remote`: The remote segment id to write to.
  * `offset_remote`: The remote offset where to write to.
  * `size`: The size of data to write.
  * `queue`: The queue where to post the write request.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_QUEUE_FULL if the requested could not be posted because the provided queue is full, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_write (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
