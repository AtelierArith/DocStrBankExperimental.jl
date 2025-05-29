```
sc_array_init_data(view, base, elem_size, elem_count)
```

Initializes an already allocated (or static) view from given plain C data. The array view returned does not require [`sc_array_reset`](@ref) (doesn't hurt though).

### Parameters

  * `view`:[in,out] Array structure to be initialized.
  * `base`:[in] The data must not be moved while view is alive.
  * `elem_size`:[in] Size of one array element in bytes.
  * `elem_count`:[in] The length of the view in element units. The view cannot be resized to exceed this length. It is not necessary to call [`sc_array_reset`](@ref) later.

### Prototype

```c
void sc_array_init_data (sc_array_t * view, void *base, size_t elem_size, size_t elem_count);
```
