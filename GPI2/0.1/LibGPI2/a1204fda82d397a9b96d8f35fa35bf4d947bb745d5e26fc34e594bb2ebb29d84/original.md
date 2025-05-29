```
gaspi_segment_size(segment_id, rank, size)
```

Get the size of a given segment on a particular rank.

### Parameters

  * `segment_id`: The segment id we are interested in.
  * `rank`: The rank.
  * `size`: Output parameter with the size of the segment.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_segment_size (const gaspi_segment_id_t segment_id, const gaspi_rank_t rank, gaspi_size_t * const size);
```
