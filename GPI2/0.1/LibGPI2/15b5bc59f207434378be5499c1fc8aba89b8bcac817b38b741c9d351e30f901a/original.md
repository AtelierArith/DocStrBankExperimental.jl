```
gaspi_read_notify(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, notification_id, queue, timeout_ms)
```

Read data from a given rank with a notification on the local side.

### Parameters

  * `segment_id_local`: The segment identifier where data to be written is located.
  * `offset_local`: The offset where the data to be written is located.
  * `rank`: The rank where to write and notify.
  * `segment_id_remote`: The remote segment identifier where to write the data to.
  * `offset_remote`: The remote offset where to write to.
  * `size`: The size of the data to write.
  * `notification_id`: The notification identifier to use.
  * `queue`: The queue where to post the request.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_QUEUE_FULL if the requested could not be posted because the provided queue is full, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_read_notify (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_notification_id_t notification_id, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
