```
gaspi_passive_send(segment_id_local, offset_local, rank, size, timeout_ms)
```

Send data of a given size to a given rank.

### Parameters

  * `segment_id_local`: The local segment identifier.
  * `offset_local`: The offset where the data to send is located.
  * `rank`: The rank to send to.
  * `size`: The size of the data to send.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_passive_send (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_size_t size, const gaspi_timeout_t timeout_ms);
```
