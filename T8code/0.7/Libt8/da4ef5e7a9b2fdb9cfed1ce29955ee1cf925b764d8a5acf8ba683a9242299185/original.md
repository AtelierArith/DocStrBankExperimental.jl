```
t8_element_destroy(ts, length, elems)
```

Deallocate an array of elements.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `length`:[in] The number of elements in the array.
  * `elems`:[in,out] On input an array of **length** many allocated element pointers. On output all these pointers will be freed. **elem** itself will not be freed by this function.

### Prototype

```c
void t8_element_destroy (const t8_eclass_scheme_c *ts, int length, t8_element_t **elems);
```
