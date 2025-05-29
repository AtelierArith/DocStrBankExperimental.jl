```
t8_element_children(ts, elem, length, c)
```

Construct all children of a given element.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] This must be a valid element, bigger than maxlevel.
  * `length`:[in] The length of the output array *c* must match the number of children.
  * `c`:[in,out] The storage for these *length* elements must exist and match the element class in the children's ordering. On output, all children are valid. It is valid to call this function with elem = c[0].

# See also

[`t8_element_num_children`](@ref)

### Prototype

```c
void t8_element_children (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int length, t8_element_t *c[]);
```
