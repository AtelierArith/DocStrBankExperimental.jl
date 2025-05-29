```
gaspi_notify_reset(segment_id_local, notification_id, old_notification_val)
```

Reset a given notification (and retrieve its value).

### Parameters

  * `segment_id_local`: The segment identifier.
  * `notification_id`: The notification identifier to reset.
  * `old_notification_val`: Output parameter with the value of the notification (before the reset).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_notify_reset (const gaspi_segment_id_t segment_id_local, const gaspi_notification_id_t notification_id, gaspi_notification_t * const old_notification_val);
```
