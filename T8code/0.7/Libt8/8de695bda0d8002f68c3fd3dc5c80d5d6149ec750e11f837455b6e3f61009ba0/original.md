```
t8_cmesh_get_tree(cmesh, ltree_id)
```

Return a pointer to a given local tree.

# Arguments

  * `cmesh`:[in] The cmesh to be queried.
  * `ltree_id`:[in] The local id of the tree that is asked for.

# Returns

A pointer to tree in *cmesh* with local id *ltree_id*. The cmesh must have at least *ltree_id* + 1 local trees when calling this function. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_ctree_t t8_cmesh_get_tree (t8_cmesh_t cmesh, t8_locidx_t ltree_id);
```
