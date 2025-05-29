```
t8_forest_ghost_get_tree_elements(forest, lghost_tree)
```

Get a pointer to the ghost element array of a ghost tree.

# Arguments

  * `forest`:[in] The forest. Ghost layer must exist.
  * `lghost_tree`:[in] The ghost tree id of a ghost tree.

# Returns

A pointer to the array of ghost elements of the tree. *forest* must be committed before calling this function.

### Prototype

```c
t8_element_array_t * t8_forest_ghost_get_tree_elements (const t8_forest_t forest, const t8_locidx_t lghost_tree);
```
