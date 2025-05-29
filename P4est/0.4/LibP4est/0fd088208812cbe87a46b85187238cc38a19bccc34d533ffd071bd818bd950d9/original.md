```
sc_io_source_destroy(source)
```

Free data source. Calls [`sc_io_source_complete`](@ref) and requires it to return no error. This is to avoid discarding buffered data that has not been passed to read.

### Parameters

  * `source`:[in,out] The source object to free.

### Returns

0 on success. Nonzero if an error is encountered or is_complete returns one.

### Prototype

```c
int sc_io_source_destroy (sc_io_source_t * source);
```
