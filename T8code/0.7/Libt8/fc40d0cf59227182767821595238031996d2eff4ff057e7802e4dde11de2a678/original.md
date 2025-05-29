```
t8_cmesh_trees_get_ghost_ext(trees, lghost_id, face_neigh, ttf)
```

Return a pointer to a specific ghost in a trees struct plus pointers to its face_neighbor and tree_to_face arrays.

# Arguments

  * `trees`:[in] The trees structure where the ghost is to be looked up.
  * `lghost_id`:[in] The local id of the ghost.
  * `face_neigh`:[out] If not NULL a pointer to the ghosts face_neighbor array is stored here on return.
  * `ttf`:[out] If not NULL a pointer to the ghosts tree_to_face array is stored here on return.

# Returns

A pointer to the tree with local id *tree*.

### Prototype

```c
t8_cghost_t t8_cmesh_trees_get_ghost_ext (t8_cmesh_trees_t trees, t8_locidx_t lghost_id, t8_gloidx_t **face_neigh, int8_t **ttf);
```
