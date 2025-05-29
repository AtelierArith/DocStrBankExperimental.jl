```
t8_element_array_index_locidx(element_array, index)
```

Return a given element in an array. Const version.

# Arguments

  * `element_array`:[in] Array of elements.
  * `index`:[in] The index of an element within the array.

# Returns

A pointer to the element stored at position *index* in *element_array*.

### Prototype

```c
const t8_element_t * t8_element_array_index_locidx (const t8_element_array_t *element_array, t8_locidx_t index);
```
