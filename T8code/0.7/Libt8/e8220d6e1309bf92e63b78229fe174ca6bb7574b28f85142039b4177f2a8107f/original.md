```
t8_cmesh_trees_get_face_info(trees, ltreeid, face, ttf)
```

Return the face neighbor of a tree at a given face and return the tree_to_face info

# Arguments

  * `trees`:[in] The trees structure where the tree is to be looked up.
  * `ltreeid`:[in] The local id of the tree.
  * `face`:[in] A face of the tree.
  * `ttf`:[out] If not NULL the tree_to_face value of the face connection.

# Returns

The face neighbor that is stored for this face

### Prototype

```c
t8_locidx_t t8_cmesh_trees_get_face_info (t8_cmesh_trees_t trees, t8_locidx_t ltreeid, int face, int8_t *ttf);
```
