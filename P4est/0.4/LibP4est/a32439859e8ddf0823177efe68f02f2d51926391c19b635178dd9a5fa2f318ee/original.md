```
sc_io_sink_destroy(sink)
```

Free data sink. Calls [`sc_io_sink_complete`](@ref) and discards the final counts. Errors from complete lead to SC_IO_ERROR_FATAL returned from this function. Call [`sc_io_sink_complete`](@ref) yourself if bytes_out is of interest.

### Parameters

  * `sink`:[in,out] The sink object to complete and free.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_sink_destroy (sc_io_sink_t * sink);
```
