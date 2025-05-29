```
t8_element_transform_face(ts, elem1, elem2, orientation, sign, is_smaller_face)
```

Suppose we have two trees that share a common face f. Given an element e that is a subface of f in one of the trees and given the orientation of the tree connection, construct the face element of the respective tree neighbor that logically coincides with e but lies in the coordinate system of the neighbor tree.

!!! note
    *elem1* and *elem2* may point to the same element.


# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem1`:[in] The face element.
  * `elem2`:[in,out] On return the face element *elem1* with respect to the coordinate system of the other tree.
  * `orientation`:[in] The orientation of the tree-tree connection.
  * `sign`:[in] Depending on the topological orientation of the two tree faces, either 0 (both faces have opposite orientation) or 1 (both faces have the same top. orientattion). t8*eclass*face_orientation
  * `is_smaller_face`:[in] Flag to declare whether *elem1* belongs to the smaller face. A face f of tree T is smaller than f' of T' if either the eclass of T is smaller or if the classes are equal and f<f'. The orientation is defined in relation to the smaller face.

# See also

[`t8_cmesh_set_join`](@ref)

### Prototype

```c
void t8_element_transform_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem1, t8_element_t *elem2, int orientation, int sign, int is_smaller_face);
```
