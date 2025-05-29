```
gaspi_segment_list(num, segment_id_list)
```

Get a list of locally allocated segments ID's.

### Parameters

  * `num`: The number of segments.
  * `segment_id_list`: Output parameter with an array wit the id's of the allocated segments.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_segment_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_list);
```
