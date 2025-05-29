```
t8_cmesh_trees_get_ghost_face_neighbor_ext(ghost, face, ttf)
```

Given a coarse ghost and a face number, return the local id of the neighbor tree together with its tree-to-face info.

# Arguments

  * `ghost`:[in] The coarse ghost.
  * `face`:[in] The face number.
  * `ttf`:[out] If not NULL it is filled with the tree-to-face value for this face.

# Returns

The global id of the neighbor tree.

### Prototype

```c
t8_gloidx_t t8_cmesh_trees_get_ghost_face_neighbor_ext (const t8_cghost_t ghost, const int face, int8_t *ttf);
```
