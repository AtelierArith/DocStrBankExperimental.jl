```
t8_element_array_copy(dest, src)
```

Copy the contents of an array into another. Both arrays must have the same eclass_scheme.

# Arguments

  * `dest`:[in] Array will be resized and get new data.
  * `src`:[in] Array used as source of new data, will not be changed.

### Prototype

```c
void t8_element_array_copy (t8_element_array_t *dest, const t8_element_array_t *src);
```
