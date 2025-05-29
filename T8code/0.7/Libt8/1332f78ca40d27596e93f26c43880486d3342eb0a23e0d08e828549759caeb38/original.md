```
t8_cmesh_trees_get_attribute(trees, ltree_id, package_id, key, size, is_ghost)
```

Return an attribute that is stored at a tree.

# Arguments

  * `trees`:[in] The trees structure.
  * `ltree_id`:[in] The local id of the tree whose attribute is querid.
  * `package_id`:[in] The package identifier of the attribute.
  * `key`:[in] The key of the attribute within all attributes of the same package identifier.
  * `size`:[out] If not NULL, the size (in bytes) of the attribute will be stored here.
  * `is_ghost`:[in] If true, then *ltree_id* is interpreted as the local_id of a ghost.

# Returns

A pointer to the queried attribute, NULL if the attribute does not exist.

### Prototype

```c
void * t8_cmesh_trees_get_attribute (const t8_cmesh_trees_t trees, const t8_locidx_t ltree_id, const int package_id, const int key, size_t *size, int is_ghost);
```
