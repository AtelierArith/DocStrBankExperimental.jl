```
t8_cmesh_trees_get_ghost(trees, lghost)
```

Return a pointer to a specific ghost in a trees struct.

# Arguments

  * `trees`:[in] The tress structure where the tree is to be looked up.
  * `lghost`:[in] The local id of the ghost.

# Returns

A pointer to the ghost with local id *ghost*.

### Prototype

```c
t8_cghost_t t8_cmesh_trees_get_ghost (t8_cmesh_trees_t trees, t8_locidx_t lghost);
```
