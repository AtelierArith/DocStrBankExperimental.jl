```
gaspi_segment_avail_local(avail_seg_id)
```

Get an available segment id (only locally).

To create/alloc a segment, the application must provide a segment id. This provides a helper function to find the next available id locally i.e. for the calling rank.

### Parameters

  * `avail_seg_id`: The available segment id.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_segment_avail_local (gaspi_segment_id_t* const avail_seg_id);
```
