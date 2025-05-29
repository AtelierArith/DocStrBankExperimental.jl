```
t8_element_array_push_count(element_array, count)
```

Enlarge an array by a number of elements.

# Arguments

  * `element_array`:[in] Array structure to be modified.
  * `count`:[in] The number of elements to add.

# Returns

Returns a pointer to the newly added elements for which t8*element*init was called.

### Prototype

```c
t8_element_t * t8_element_array_push_count (t8_element_array_t *element_array, size_t count);
```
