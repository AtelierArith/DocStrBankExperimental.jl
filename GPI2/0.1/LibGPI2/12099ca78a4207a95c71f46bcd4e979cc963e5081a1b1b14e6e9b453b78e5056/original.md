```
gaspi_notify_waitsome(segment_id_local, notification_begin, num, first_id, timeout_ms)
```

Wait for some notification.

### Parameters

  * `segment_id_local`: The segment identifier.
  * `notification_begin`: The notification id where to start to wait.
  * `num`: The number of notifications to wait for.
  * `first_id`: Output parameter with the identifier of a received notification.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_notify_waitsome (const gaspi_segment_id_t segment_id_local, const gaspi_notification_id_t notification_begin, const gaspi_number_t num, gaspi_notification_id_t * const first_id, const gaspi_timeout_t timeout_ms);
```
