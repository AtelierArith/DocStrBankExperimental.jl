```
t8_element_num_face_children(ts, elem, face)
```

Compute the number of children of an element's face when the element is refined.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.
  * `face`:[in] A face of *elem*.

# Returns

The number of children of *face* if *elem* is to be refined.

### Prototype

```c
int t8_element_num_face_children (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
