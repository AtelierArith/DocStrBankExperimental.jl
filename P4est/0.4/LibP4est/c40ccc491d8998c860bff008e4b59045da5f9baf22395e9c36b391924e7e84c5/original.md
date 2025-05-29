```
sc_io_source_align(source, bytes_align)
```

Align source to a byte boundary by skipping.

### Parameters

  * `source`:[in,out] The source object to align.
  * `bytes_align`:[in] Byte boundary.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_source_align (sc_io_source_t * source, size_t bytes_align);
```
