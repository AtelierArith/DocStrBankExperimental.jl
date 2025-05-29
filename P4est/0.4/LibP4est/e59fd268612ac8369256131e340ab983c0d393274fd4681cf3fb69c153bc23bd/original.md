```
sc_mempool_new_zero_and_persist(elem_size)
```

Creates a new mempool structure with the zero_and_persist option on. The memory of newly created elements is zero'd out, and the contents of an element are not touched between freeing and re-returning it.

### Parameters

  * `elem_size`:[in] Size of one element in bytes.

### Returns

Returns an allocated and initialized memory pool.

### Prototype

```c
sc_mempool_t *sc_mempool_new_zero_and_persist (size_t elem_size);
```
