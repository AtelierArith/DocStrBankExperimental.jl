```
gaspi_passive_receive(segment_id_local, offset_local, rem_rank, size, timeout_ms)
```

Receive data of a given size from any rank.

### Parameters

  * `segment_id_local`: The segment where to place the received data.
  * `offset_local`: The local offset where to place the received data.
  * `rem_rank`: Output parameter with the sender (rank).
  * `size`: The size to receive.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_passive_receive (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, gaspi_rank_t * const rem_rank, const gaspi_size_t size, const gaspi_timeout_t timeout_ms);
```
