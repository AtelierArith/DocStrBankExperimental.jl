```
sc_array_new_count(elem_size, elem_count)
```

Creates a new array structure with a given length (number of elements).

### Parameters

  * `elem_size`:[in] Size of one array element in bytes.
  * `elem_count`:[in] Initial number of array elements.

### Returns

Return an allocated array with allocated but uninitialized elements.

### Prototype

```c
sc_array_t *sc_array_new_count (size_t elem_size, size_t elem_count);
```
