```
t8_element_array_init_size(element_array, scheme, num_elements)
```

Initializes an already allocated (or static) array structure and allocates a given number of elements and initializes them with t8*element*init.

# Arguments

  * `element_array`:[in,out] Array structure to be initialized.
  * `scheme`:[in] The eclass scheme of which elements should be stored.
  * `num_elements`:[in] Number of initial array elements.

### Prototype

```c
void t8_element_array_init_size (t8_element_array_t *element_array, t8_eclass_scheme_c *scheme, size_t num_elements);
```
