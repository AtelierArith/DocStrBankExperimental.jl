```
gaspi_write_list_notify(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, segment_id_notification, notification_id, notification_value, queue, timeout_ms)
```

Write to different locations and notify that particular rank.

### Parameters

  * `num`: The number of elements in the list.
  * `segment_id_local`: The list of local segments where data is located.
  * `offset_local`: The list of local offsets where data to write is located.
  * `rank`: The rank where to write the list and notification.
  * `segment_id_remote`: The list of remote segments where to write.
  * `offset_remote`: The list of remote offsets where to write.
  * `size`: The list of sizes to write.
  * `segment_id_notification`: The segment id used for notification.
  * `notification_id`: The notification identifier to use.
  * `notification_value`: The notification value to send.
  * `queue`: The queue where to post the request.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_QUEUE_FULL if the requested could not be posted because the provided queue is full, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_write_list_notify (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_segment_id_t segment_id_notification, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
