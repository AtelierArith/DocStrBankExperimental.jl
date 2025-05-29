```
pgaspi_passive_receive(segment_id_local, offset_local, rem_rank, size, timeout_ms)
```

### プロトタイプ

```c
gaspi_return_t pgaspi_passive_receive (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, gaspi_rank_t * const rem_rank, const gaspi_size_t size, const gaspi_timeout_t timeout_ms);
```
