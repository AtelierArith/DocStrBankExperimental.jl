```
t8_element_array_init_copy(element_array, scheme, data, num_elements)
```

Initializes an already allocated (or static) array structure and copy an existing array of [`t8_element_t`](@ref) into it.

# Arguments

  * `element_array`:[in,out] Array structure to be initialized.
  * `scheme`:[in] The eclass scheme of which elements should be stored.
  * `data`:[in] An array of [`t8_element_t`](@ref) which will be copied into *element_array*. The elements in *data* must belong to *scheme* and must be properly initialized with either t8*element*new or t8*element*init.
  * `num_elements`:[in] Number of elements in *data* to be copied.

### Prototype

```c
void t8_element_array_init_copy (t8_element_array_t *element_array, t8_eclass_scheme_c *scheme, t8_element_t *data, size_t num_elements);
```
