```
t8_forest_element_face_neighbor(forest, ltreeid, elem, neigh, neigh_scheme, face, neigh_face)
```

Construct the face neighbor of an element, possibly across tree boundaries. Returns the global tree-id of the tree in which the neighbor element lies in.

# Arguments

  * `elem`:[in] The element to be considered.
  * `neigh`:[in,out] On input an allocated element of the scheme of the face_neighbors eclass. On output, this element's data is filled with the data of the face neighbor. If the neighbor does not exist the data could be modified arbitrarily.
  * `neigh_scheme`:[in] The eclass scheme of *neigh*.
  * `face`:[in] The number of the face along which the neighbor should be constructed.
  * `neigh_face`:[out] The number of the face viewed from perspective of *neigh*.

# Returns

The global tree-id of the tree in which *neigh* is in. -1 if there exists no neighbor across that face.

### Prototype

```c
t8_gloidx_t t8_forest_element_face_neighbor (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *elem, t8_element_t *neigh, t8_eclass_scheme_c *neigh_scheme, int face, int *neigh_face);
```
