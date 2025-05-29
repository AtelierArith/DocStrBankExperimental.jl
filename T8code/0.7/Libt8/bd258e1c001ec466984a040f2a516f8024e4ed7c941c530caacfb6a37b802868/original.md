```
t8_element_is_root_boundary(ts, elem, face)
```

Compute whether a given element shares a given face with its root tree.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The input element.
  * `face`:[in] A face of *elem*.

# Returns

True if *face* is a subface of the element's root element.

### Prototype

```c
int t8_element_is_root_boundary (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
