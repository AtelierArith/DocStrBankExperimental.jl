```
t8_element_array_truncate(element_array)
```

Sets the array count to zero, but does not free elements.

!!! note
    This is intended to allow an t8_element_array to be used as a reusable buffer, where the "high water mark" of the buffer is preserved, so that O(log (max n)) reallocs occur over the life of the buffer.


# Arguments

  * `element_array`:[in,out] Element array structure to be truncated.

### Prototype

```c
void t8_element_array_truncate (t8_element_array_t *element_array);
```
