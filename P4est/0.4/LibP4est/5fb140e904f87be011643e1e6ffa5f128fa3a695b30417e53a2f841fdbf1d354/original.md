```
sc_array_new_data(base, elem_size, elem_count)
```

Creates a new view of an existing plain C array.

### Parameters

  * `base`:[in] The data must not be moved while view is alive.
  * `elem_size`:[in] Size of one array element in bytes.
  * `elem_count`:[in] The length of the view in element units. The view cannot be resized to exceed this length.

### Prototype

```c
sc_array_t *sc_array_new_data (void *base, size_t elem_size, size_t elem_count);
```
