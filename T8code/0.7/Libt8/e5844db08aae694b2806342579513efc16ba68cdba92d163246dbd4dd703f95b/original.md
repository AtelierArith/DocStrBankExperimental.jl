```
t8_cmesh_tree_to_face_decode(dimension, tree_to_face, face, orientation)
```

Given a tree-to-face value, get its encoded face number and orientation.

!!! note
    This function is the inverse operation of t8*cmesh*tree*to*face*encode If F = t8\*eclass_max_num_faces[dimension], we get orientation = tree_to_face / F face = tree_to_face % F


# Arguments

  * `dimension`:[in] The dimension of the corresponding eclasses.
  * `tree_to_face`:[in] A tree-to-face value
  * `face`:[out] On output filled with the stored face value.
  * `orientation`:[out] On output filled with the stored orientation value.

### Prototype

```c
void t8_cmesh_tree_to_face_decode (const int dimension, const int8_t tree_to_face, int *face, int *orientation);
```
