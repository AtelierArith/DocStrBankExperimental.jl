```
sc_io_sink_align(sink, bytes_align)
```

Align sink to a byte boundary by writing zeros.

### Parameters

  * `sink`:[in,out] The sink object to align.
  * `bytes_align`:[in] Byte boundary.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_sink_align (sc_io_sink_t * sink, size_t bytes_align);
```
