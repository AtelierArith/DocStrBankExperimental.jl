```
t8_forest_get_tree(forest, ltree_id)
```

Return a pointer to a tree in a forest.

# Arguments

  * `forest`:[in] The forest.
  * `ltree_id`:[in] The local id of the tree.

# Returns

A pointer to the tree with local id *ltree_id*. *forest* must be committed before calling this function.

### Prototype

```c
t8_tree_t t8_forest_get_tree (const t8_forest_t forest, const t8_locidx_t ltree_id);
```
