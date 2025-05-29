```
sc_array_resize(array, new_count)
```

Sets the element count to new_count. If the array is not a view, reallocation takes place occasionally. If the array is a view, new_count must not be greater than the element count of the view when it was created. The original offset of the view cannot be changed.

### Parameters

  * `array`:[in,out] The element count and address is modified.
  * `new_count`:[in] New element count of the array. If it is zero and the array is not a view, the effect equals sc*array*reset.

### Prototype

```c
void sc_array_resize (sc_array_t * array, size_t new_count);
```
