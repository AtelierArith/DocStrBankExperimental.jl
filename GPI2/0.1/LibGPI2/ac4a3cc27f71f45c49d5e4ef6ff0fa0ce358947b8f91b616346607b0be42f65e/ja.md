```
pgaspi_notify(segment_id_remote, rank, notification_id, notification_value, queue, timeout_ms)
```

### プロトタイプ

```c
gaspi_return_t pgaspi_notify (const gaspi_segment_id_t segment_id_remote, const gaspi_rank_t rank, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
