```
sc_io_source_read(source, data, bytes_avail, bytes_out)
```

Read data from a source. The internal counters source->bytes_in and source->bytes_out are updated. Data is read until the data buffer has not enough room anymore, or source becomes empty. It is possible that data already read internally remains in the source object for the next call. Call [`sc_io_source_complete`](@ref) and check its return value to find out. Returns an error if bytes_out is NULL and less than bytes_avail are read.

### Parameters

  * `source`:[in,out] The source object to read from.
  * `data`:[in] Data buffer for reading from sink. If NULL the output data will be thrown away.
  * `bytes_avail`:[in] Number of bytes available in data buffer.
  * `bytes_out`:[in,out] If not NULL, byte count read into data buffer. Otherwise, requires to read exactly bytes_avail.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_source_read (sc_io_source_t * source, void *data, size_t bytes_avail, size_t * bytes_out);
```
