```
sc_array_new_view(array, offset, length)
```

Creates a new view of an existing [`sc_array_t`](@ref).

### Parameters

  * `array`:[in] The array must not be resized while view is alive.
  * `offset`:[in] The offset of the viewed section in element units. This offset cannot be changed until the view is reset.
  * `length`:[in] The length of the viewed section in element units. The view cannot be resized to exceed this length.

### Prototype

```c
sc_array_t *sc_array_new_view (sc_array_t * array, size_t offset, size_t length);
```
