```
sc_io_sink_complete(sink, bytes_in, bytes_out)
```

Flush all buffered output data to sink. This function may return SC_IO_ERROR_AGAIN if another write is required. Currently this may happen if BUFFER requires an integer multiple of bytes. If successful, the updated value of bytes read and written is returned in bytes_in/out, and the sink status is reset as if the sink had just been created. In particular, the bytes counters are reset to zero. The internal state of the sink is not changed otherwise. It is legal to continue writing to the sink hereafter. The sink actions taken depend on its type. BUFFER, FILEFILE: none. FILENAME: call fclose on sink->file.

### Parameters

  * `sink`:[in,out] The sink object to write to.
  * `bytes_in`:[in,out] Bytes received since the last new or complete call. May be NULL.
  * `bytes_out`:[in,out] Bytes written since the last new or complete call. May be NULL.

### Returns

0 if completed, nonzero on error.

### Prototype

```c
int sc_io_sink_complete (sc_io_sink_t * sink, size_t * bytes_in, size_t * bytes_out);
```
