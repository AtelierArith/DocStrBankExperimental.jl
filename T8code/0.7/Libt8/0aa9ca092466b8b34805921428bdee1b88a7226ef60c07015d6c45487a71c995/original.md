```
t8_cmesh_get_tree_class(cmesh, ltree_id)
```

Return the eclass of a given local tree. TODO: Should we refer to indices or consequently use ctree_t?

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `tree_id`:[in] The local id of the tree whose eclass will be returned.

# Returns

The eclass of the given tree. TODO: Call tree ids ltree_id or gtree_id etc. instead of tree_id. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_eclass_t t8_cmesh_get_tree_class (t8_cmesh_t cmesh, t8_locidx_t ltree_id);
```
