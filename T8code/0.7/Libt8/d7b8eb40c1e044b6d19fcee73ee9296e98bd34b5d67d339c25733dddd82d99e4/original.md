```
t8_cmesh_tree_to_face_encode(dimension, face, orientation)
```

Compute the tree-to-face information given a face and orientation value of a face connection.

# Arguments

  * `dimension`:[in] The dimension of the corresponding eclasses.
  * `face`:[in] A face number
  * `orientation`:[in] A face-to-face orientation.

# Returns

The tree-to-face entry corresponding to the face/orientation combination. It is computed as t8_eclass_max_num_faces[dimension] * orientation + face

### Prototype

```c
int8_t t8_cmesh_tree_to_face_encode (const int dimension, const t8_locidx_t face, const int orientation);
```
