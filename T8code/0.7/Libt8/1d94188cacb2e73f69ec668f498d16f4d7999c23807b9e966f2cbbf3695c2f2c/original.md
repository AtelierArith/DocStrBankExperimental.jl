```
t8_element_array_new_count(scheme, num_elements)
```

Creates a new array structure with a given length (number of elements) and calls t8*element*new for those elements.

# Arguments

  * `scheme`:[in] The eclass scheme of which elements should be stored.
  * `num_elements`:[in] Initial number of array elements.

# Returns

Return an allocated array with allocated and initialized elements for which t8*element*new was called.

### Prototype

```c
t8_element_array_t * t8_element_array_new_count (t8_eclass_scheme_c *scheme, size_t num_elements);
```
