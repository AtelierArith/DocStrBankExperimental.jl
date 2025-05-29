```
sc_array_init_size(array, elem_size, elem_count)
```

Initializes an already allocated (or static) array structure and allocates a given number of elements. Deprecated: use sc*array*init_count.

### Parameters

  * `array`:[in,out] Array structure to be initialized.
  * `elem_size`:[in] Size of one array element in bytes.
  * `elem_count`:[in] Number of initial array elements.

### Prototype

```c
void sc_array_init_size (sc_array_t * array, size_t elem_size, size_t elem_count);
```
