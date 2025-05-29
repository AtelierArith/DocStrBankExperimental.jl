```
p8est_connectivity_inflate(buffer)
```

Create new connectivity from a memory buffer.

### Parameters

  * `buffer`:[in] The connectivity is created from this memory buffer.

### Returns

The newly created connectivity, or NULL on error.

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_inflate (sc_array_t * buffer);
```
