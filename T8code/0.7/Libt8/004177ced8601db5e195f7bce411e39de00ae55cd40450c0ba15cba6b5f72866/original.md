```
t8_forest_tree_is_local(forest, local_tree)
```

Check whether a given tree id belongs to a local tree in a forest.

# Arguments

  * `forest`:[in] The forest.
  * `local_tree`:[in] A tree id.

# Returns

True if and only if the id *local_tree* belongs to a local tree of *forest*. *forest* must be committed before calling this function.

### Prototype

```c
int t8_forest_tree_is_local (const t8_forest_t forest, const t8_locidx_t local_tree);
```
