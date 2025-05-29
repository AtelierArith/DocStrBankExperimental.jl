```
pgaspi_write_notify(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, notification_id, notification_value, queue, timeout_ms)
```

### Prototype

```c
gaspi_return_t pgaspi_write_notify (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
