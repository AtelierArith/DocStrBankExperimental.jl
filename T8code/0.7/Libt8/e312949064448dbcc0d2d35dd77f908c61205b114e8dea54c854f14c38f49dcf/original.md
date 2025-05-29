```
t8_cmesh_trees_get_ghost_local_id(trees, global_id)
```

Given the global tree id of a ghost tree in a trees structure, return its local ghost id.

# Arguments

  * `trees`:[in] The trees structure.
  * `global_id`:[in] A global tree id.

# Returns

The local id of the tree *global_id* if it is a ghost in *trees*. A negative number if it isn't. The local id is a number l with num_local_trees <= *l* < num_local_trees + num_ghosts

### Prototype

```c
t8_locidx_t t8_cmesh_trees_get_ghost_local_id (t8_cmesh_trees_t trees, t8_gloidx_t global_id);
```
