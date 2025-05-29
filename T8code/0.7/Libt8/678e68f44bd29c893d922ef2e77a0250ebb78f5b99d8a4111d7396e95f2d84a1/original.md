```
t8_cmesh_trees_get_face_neighbor(tree, face)
```

Given a coarse tree and a face number, return the local id of the neighbor tree.

# Arguments

  * `tree.`:[in] The coarse tree.
  * `face.`:[in] The face number.

# Returns

The local id of the neighbor tree.

### Prototype

```c
t8_locidx_t t8_cmesh_trees_get_face_neighbor (const t8_ctree_t tree, const int face);
```
