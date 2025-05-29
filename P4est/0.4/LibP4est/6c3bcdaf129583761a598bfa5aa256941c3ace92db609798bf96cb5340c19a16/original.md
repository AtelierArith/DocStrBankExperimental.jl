```
sc_io_source_activate_mirror(source)
```

Activate a buffer that mirrors (i.e., stores) the data that was read.

### Parameters

  * `source`:[in,out] The source object to activate mirror in.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int sc_io_source_activate_mirror (sc_io_source_t * source);
```
