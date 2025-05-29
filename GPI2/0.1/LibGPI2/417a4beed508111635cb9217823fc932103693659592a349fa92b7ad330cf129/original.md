```
gaspi_notify(segment_id_remote, rank, notification_id, notification_value, queue, timeout_ms)
```

Post a notification with a particular value to a given rank.

### Parameters

  * `segment_id_remote`: The remote segment id.
  * `rank`: The rank to notify.
  * `notification_id`: The notification id.
  * `notification_value`: The notification value.
  * `queue`: The queue to post the notification request.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_notify (const gaspi_segment_id_t segment_id_remote, const gaspi_rank_t rank, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
