```
sc_io_source_read_mirror(source, data, bytes_avail, bytes_out)
```

Read data from the source's mirror. Same behaviour as [`sc_io_source_read`](@ref).

### Parameters

  * `source`:[in,out] The source object to read mirror data from.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_source_read_mirror (sc_io_source_t * source, void *data, size_t bytes_avail, size_t * bytes_out);
```
