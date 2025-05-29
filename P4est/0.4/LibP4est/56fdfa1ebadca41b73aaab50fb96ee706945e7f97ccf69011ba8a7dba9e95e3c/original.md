```
sc_array_init_view(view, array, offset, length)
```

Initializes an already allocated (or static) view from existing [`sc_array_t`](@ref). The array view returned does not require [`sc_array_reset`](@ref) (doesn't hurt though).

### Parameters

  * `view`:[in,out] Array structure to be initialized.
  * `array`:[in] The array must not be resized while view is alive.
  * `offset`:[in] The offset of the viewed section in element units. This offset cannot be changed until the view is reset.
  * `length`:[in] The length of the view in element units. The view cannot be resized to exceed this length. It is not necessary to call [`sc_array_reset`](@ref) later.

### Prototype

```c
void sc_array_init_view (sc_array_t * view, sc_array_t * array, size_t offset, size_t length);
```
