```
t8_element_face_neighbor_inside(ts, elem, neigh, face, neigh_face)
```

Construct the face neighbor of a given element if this face neighbor is inside the root tree. Return 0 otherwise.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The element to be considered.
  * `neigh`:[in,out] If the face neighbor of *elem* along *face* is inside the root tree, this element's data is filled with the data of the face neighbor. Otherwise the data can be modified arbitrarily.
  * `face`:[in] The number of the face along which the neighbor should be constructed.
  * `neigh_face`:[out] The number of *face* as viewed from *neigh*. An arbitrary value, if the neighbor is not inside the root tree.

# Returns

True if *neigh* is inside the root tree. False if not. In this case *neigh*'s data can be arbitrary on output.

### Prototype

```c
int t8_element_face_neighbor_inside (const t8_eclass_scheme_c *ts, const t8_element_t *elem, t8_element_t *neigh, int face, int *neigh_face);
```
