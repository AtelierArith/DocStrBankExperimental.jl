```
t8_element_array_index_locidx_mutable(element_array, index)
```

Return a given element in an array. Mutable version.

# Arguments

  * `element_array`:[in] Array of elements.
  * `index`:[in] The index of an element within the array.

# Returns

A pointer to the element stored at position *index* in *element_array*.

### Prototype

```c
t8_element_t * t8_element_array_index_locidx_mutable (t8_element_array_t *element_array, t8_locidx_t index);
```
