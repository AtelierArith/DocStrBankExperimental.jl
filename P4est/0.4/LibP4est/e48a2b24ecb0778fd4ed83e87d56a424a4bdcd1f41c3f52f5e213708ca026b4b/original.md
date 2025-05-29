```
sc_io_source_complete(source, bytes_in, bytes_out)
```

Determine whether all data buffered from source has been returned by read. If it returns SC_IO_ERROR_AGAIN, another [`sc_io_source_read`](@ref) is required. If the call returns no error, the internal counters source->bytes_in and source->bytes_out are returned to the caller if requested, and reset to 0. The internal state of the source is not changed otherwise. It is legal to continue reading from the source hereafter.

### Parameters

  * `source`:[in,out] The source object to read from.
  * `bytes_in`:[in,out] If not NULL and true is returned, the total size of the data sourced.
  * `bytes_out`:[in,out] If not NULL and true is returned, total bytes passed out by source_read.

### Returns

SC_IO_ERROR_AGAIN if buffered data remaining. Otherwise return ERROR_NONE and reset counters.

### Prototype

```c
int sc_io_source_complete (sc_io_source_t * source, size_t * bytes_in, size_t * bytes_out);
```
