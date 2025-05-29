```
t8_element_array_reset(element_array)
```

Sets the array count to zero and frees all elements.

!!! note
    Calling [`t8_element_array_init`](@ref), then any array operations, then [`t8_element_array_reset`](@ref) is memory neutral.


# Arguments

  * `element_array`:[in,out] Array structure to be reset.

### Prototype

```c
void t8_element_array_reset (t8_element_array_t *element_array);
```
