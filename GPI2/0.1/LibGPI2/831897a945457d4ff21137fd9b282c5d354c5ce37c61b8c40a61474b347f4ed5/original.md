```
pgaspi_notify_waitsome(segment_id_local, notification_begin, num, first_id, timeout_ms)
```

### Prototype

```c
gaspi_return_t pgaspi_notify_waitsome (const gaspi_segment_id_t segment_id_local, const gaspi_notification_id_t notification_begin, const gaspi_number_t num, gaspi_notification_id_t * const first_id, const gaspi_timeout_t timeout_ms);
```
