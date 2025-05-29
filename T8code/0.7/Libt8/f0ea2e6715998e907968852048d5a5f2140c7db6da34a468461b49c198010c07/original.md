```
t8_element_array_get_data(element_array)
```

Return a const pointer to the real data array stored in a t8_element_array.

# Arguments

  * `element_array`:[in] Array structure.

# Returns

A pointer to the stored data. If the number of stored elements is 0, then NULL is returned.

### Prototype

```c
const t8_element_t * t8_element_array_get_data (const t8_element_array_t *element_array);
```
