```
t8_element_max_num_faces(ts, elem)
```

Compute the maximum number of faces of a given element and all of its descendants.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.

# Returns

The number of faces of *element*.

### Prototype

```c
int t8_element_max_num_faces (const t8_eclass_scheme_c *ts, const t8_element_t *elem);
```
