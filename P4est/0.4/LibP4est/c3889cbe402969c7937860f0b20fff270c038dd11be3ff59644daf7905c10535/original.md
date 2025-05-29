```
sc_io_sink_write(sink, data, bytes_avail)
```

Write data to a sink. Data may be buffered and sunk in a later call. The internal counters sink->bytes_in and sink->bytes_out are updated.

### Parameters

  * `sink`:[in,out] The sink object to write to.
  * `data`:[in] Data passed into sink.
  * `bytes_avail`:[in] Number of data bytes passed in.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_sink_write (sc_io_sink_t * sink, const void *data, size_t bytes_avail);
```
