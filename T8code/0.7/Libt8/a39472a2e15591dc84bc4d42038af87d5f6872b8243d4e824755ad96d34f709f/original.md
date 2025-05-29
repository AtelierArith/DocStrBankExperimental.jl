```
t8_element_face_shape(ts, elem, face)
```

Compute the shape of the face of an element.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.
  * `face`:[in] A face of *elem*.

# Returns

The element shape of the face. I.e. T8_ECLASS_LINE for quads, T8_ECLASS_TRIANGLE for tets and depending on the face number either T8_ECLASS_QUAD or T8_ECLASS_TRIANGLE for prisms.

### Prototype

```c
t8_element_shape_t t8_element_face_shape (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
