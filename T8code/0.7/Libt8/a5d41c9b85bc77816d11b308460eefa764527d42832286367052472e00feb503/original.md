```
t8_cmesh_trees_get_face_neighbor_ext(tree, face, ttf)
```

Given a coarse tree and a face number, return the local id of the neighbor tree together with its tree-to-face info.

# Arguments

  * `tree`:[in] The coarse tree.
  * `face`:[in] The face number.
  * `ttf`:[out] If not NULL it is filled with the tree-to-face value for this face.

# Returns

The local id of the neighbor tree.

### Prototype

```c
t8_locidx_t t8_cmesh_trees_get_face_neighbor_ext (const t8_ctree_t tree, const int face, int8_t *ttf);
```
