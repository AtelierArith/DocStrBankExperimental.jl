```
t8_cmesh_get_local_id(cmesh, global_id)
```

Return the local id of a give global tree.

# Arguments

  * `cmesh`:[in] The cmesh.
  * `global_id`:[in] A global tree id.

# Returns

Either a value l 0 <= *l* < num_local_trees if *global_id* corresponds to a local tree, or num_local_trees <= *l* < num_local_trees + num_ghosts if *global_id* corresponds to a ghost trees, or negative if *global_id* neither matches a local nor a ghost tree.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_locidx_t t8_cmesh_get_local_id (t8_cmesh_t cmesh, t8_gloidx_t global_id);
```
