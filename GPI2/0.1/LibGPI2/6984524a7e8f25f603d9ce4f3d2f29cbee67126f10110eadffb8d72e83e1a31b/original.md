```
gaspi_segment_register(segment_id, rank, timeout_ms)
```

Register a segment for communication. In case of success, the segment can be used for communication between the involved ranks.

### Parameters

  * `segment_id`: Segment identified to be registered.
  * `rank`: The rank to register this segment with.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_segment_register (const gaspi_segment_id_t segment_id, const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
