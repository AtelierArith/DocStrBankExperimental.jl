```
sc_array_init_count(array, elem_size, elem_count)
```

Initializes an already allocated (or static) array structure and allocates a given number of elements. This function supersedes sc*array*init_size.

### Parameters

  * `array`:[in,out] Array structure to be initialized.
  * `elem_size`:[in] Size of one array element in bytes.
  * `elem_count`:[in] Number of initial array elements.

### Prototype

```c
void sc_array_init_count (sc_array_t * array, size_t elem_size, size_t elem_count);
```
