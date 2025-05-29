```
t8_cmesh_trees_get_tree_ext(trees, ltree_id, face_neigh, ttf)
```

Return a pointer to a specific tree in a trees struct plus pointers to its face_neighbor and tree_to_face arrays.

# Arguments

  * `trees`:[in] The trees structure where the tree is to be looked up.
  * `ltree_id`:[in] The local id of the tree.
  * `face_neigh`:[out] If not NULL a pointer to the trees face_neighbor array is stored here on return.
  * `ttf`:[out] If not NULL a pointer to the trees tree_to_face array is stored here on return.

# Returns

A pointer to the tree with local id *tree*.

### Prototype

```c
t8_ctree_t t8_cmesh_trees_get_tree_ext (t8_cmesh_trees_t trees, t8_locidx_t ltree_id, t8_locidx_t **face_neigh, int8_t **ttf);
```
