```
t8_element_array_resize(element_array, new_count)
```

Change the number of elements stored in an element array.

!!! note
    If *new_count* is larger than the number of current elements on *element_array*, then t8*element*init is called for the new elements.


# Arguments

  * `element_array`:[in,out] The element array to be modified.
  * `new_count`:[in] The new element count of the array. If it is zero the effect equals t8*element*array_reset.

### Prototype

```c
void t8_element_array_resize (t8_element_array_t *element_array, size_t new_count);
```
