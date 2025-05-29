```
t8_cmesh_tree_face_is_boundary(cmesh, ltree_id, face)
```

Query whether a face of a local tree or ghost is at the domain boundary.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `ltree_id`:[in] The local id of a tree.
  * `face`:[in] The number of a face of the tree.

# Returns

True if the face is at the domain boundary. False otherwise. *cmesh* must be committed before calling this function.

### Prototype

```c
int t8_cmesh_tree_face_is_boundary (t8_cmesh_t cmesh, t8_locidx_t ltree_id, int face);
```
