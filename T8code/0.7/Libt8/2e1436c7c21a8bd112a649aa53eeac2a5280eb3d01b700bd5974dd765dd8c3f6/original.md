```
t8_element_face_parent_face(ts, elem, face)
```

Given a face of an element return the face number of the parent of the element that matches the element's face. Or return -1 if no face of the parent matches the face.

!!! note
    For the root element this function always returns *face*.


# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element.
  * `face`:[in] Then number of the face.

# Returns

If *face* of *elem* is also a face of *elem*'s parent, the face number of this face. Otherwise -1.

### Prototype

```c
int t8_element_face_parent_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
