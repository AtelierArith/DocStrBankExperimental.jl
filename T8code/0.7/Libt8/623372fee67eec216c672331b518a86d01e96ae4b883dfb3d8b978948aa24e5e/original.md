```
t8_element_array_get_array_mutable(element_array)
```

Return a mutable pointer to the [`sc_array`](@ref) stored in a t8_element_array.

!!! note
    The data can be modified.


# Arguments

  * `element_array`:[in] Array structure.

# Returns

A pointer to the [`sc_array`](@ref) storing the data.

### Prototype

```c
sc_array_t * t8_element_array_get_array_mutable (t8_element_array_t *element_array);
```
