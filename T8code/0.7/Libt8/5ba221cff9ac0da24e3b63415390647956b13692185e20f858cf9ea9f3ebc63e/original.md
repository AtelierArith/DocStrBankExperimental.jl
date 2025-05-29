```
t8_element_array_get_array(element_array)
```

Return a const pointer to the [`sc_array`](@ref) stored in a t8_element_array.

!!! note
    The data cannot be modified.


# Arguments

  * `element_array`:[in] Array structure.

# Returns

A const pointer to the [`sc_array`](@ref) storing the data.

### Prototype

```c
const sc_array_t * t8_element_array_get_array (const t8_element_array_t *element_array);
```
