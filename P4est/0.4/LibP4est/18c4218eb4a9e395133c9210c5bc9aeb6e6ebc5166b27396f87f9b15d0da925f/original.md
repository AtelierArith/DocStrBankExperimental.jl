```
p4est_connectivity_source(source)
```

Read connectivity from a source object.

### Parameters

  * `source`:[in,out] The connectivity is read from this source.

### Returns

The newly created connectivity, or NULL on error.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_source (sc_io_source_t * source);
```
