```
t8_element_extrude_face(ts, face, face_scheme, elem, root_face)
```

Given a boundary face inside a root tree's face construct the element inside the root tree that has the given face as a face.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `face`:[in] A face element.
  * `face_scheme`:[in] The scheme for the face element.
  * `elem`:[in,out] An allocated element. The entries will be filled with the data of the element that has *face* as a face and lies within the root tree.
  * `root_face`:[in] The index of the face of the root tree in which *face* lies.

# Returns

The face number of the face of *elem* that coincides with *face*.

### Prototype

```c
int t8_element_extrude_face (const t8_eclass_scheme_c *ts, const t8_element_t *face, const t8_eclass_scheme_c *face_scheme, t8_element_t *elem, int root_face);
```
