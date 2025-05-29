```
t8_element_boundary_face(ts, elem, face, boundary, boundary_scheme)
```

Construct the boundary element at a specific face.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The input element.
  * `face`:[in] The index of the face of which to construct the boundary element.
  * `boundary`:[in,out] An allocated element of dimension of *element* minus 1. The entries will be filled with the entries of the face of *element*.
  * `boundary_scheme`:[in] The scheme for the eclass of the boundary face. If *elem* is of class T8_ECLASS_VERTEX, then *boundary* must be NULL and will not be modified.

### Prototype

```c
void t8_element_boundary_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *boundary, const t8_eclass_scheme_c *boundary_scheme);
```
