```
t8_cmesh_trees_get_tree(trees, ltree)
```

Return a pointer to a specific tree in a trees struct.

# Arguments

  * `trees`:[in] The tress structure where the tree is to be looked up.
  * `ltree`:[in] The local id of the tree.

# Returns

A pointer to the tree with local id *tree*.

### Prototype

```c
t8_ctree_t t8_cmesh_trees_get_tree (t8_cmesh_trees_t trees, t8_locidx_t ltree);
```
