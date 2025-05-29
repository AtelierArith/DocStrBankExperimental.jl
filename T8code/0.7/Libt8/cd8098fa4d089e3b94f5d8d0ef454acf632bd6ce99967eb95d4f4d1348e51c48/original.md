```
t8_element_array_push(element_array)
```

Enlarge an array by one element.

# Arguments

  * `element_array`:[in] Array structure to be modified.

# Returns

Returns a pointer to a newly added element for which t8*element*init was called.

### Prototype

```c
t8_element_t * t8_element_array_push (t8_element_array_t *element_array);
```
