```
t8_element_array_init_data(view, base, scheme, elem_count)
```

Initializes an already allocated (or static) view from given plain C data (array of [`t8_element_t`](@ref)). The array view returned does not require [`t8_element_array_reset`](@ref) (doesn't hurt though).

# Arguments

  * `view`:[in,out] Array structure to be initialized.
  * `base`:[in] The data must not be moved while view is alive. Must be an array of [`t8_element_t`](@ref) corresponding to *scheme*.
  * `scheme`:[in] The eclass scheme of the elements stored in *base*.
  * `elem_count`:[in] The length of the view in element units. The view cannot be resized to exceed this length. It is not necessary to call [`t8_element_array_reset`](@ref) later.

### Prototype

```c
void t8_element_array_init_data (t8_element_array_t *view, t8_element_t *base, t8_eclass_scheme_c *scheme, size_t elem_count);
```
