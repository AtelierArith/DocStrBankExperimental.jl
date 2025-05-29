```
pgaspi_write(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

### Prototype

```c
gaspi_return_t pgaspi_write (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
