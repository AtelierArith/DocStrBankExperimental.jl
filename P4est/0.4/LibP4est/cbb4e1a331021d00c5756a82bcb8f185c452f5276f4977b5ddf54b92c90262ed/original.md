```
sc_mempool_new(elem_size)
```

Creates a new mempool structure with the zero_and_persist option off. The contents of any elements returned by sc_mempool_alloc are undefined.

### Parameters

  * `elem_size`:[in] Size of one element in bytes.

### Returns

Returns an allocated and initialized memory pool.

### Prototype

```c
sc_mempool_t *sc_mempool_new (size_t elem_size);
```
