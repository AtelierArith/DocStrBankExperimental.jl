```
t8_cmesh_get_global_id(cmesh, local_id)
```

Return the global id of a given local tree or ghost.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `local_id`:[in] The local id of a tree or a ghost. If *local_id* < cmesh.num_local_trees then it is a tree, otherwise a ghost.

# Returns

The global id of the tree/ghost.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_gloidx_t t8_cmesh_get_global_id (t8_cmesh_t cmesh, t8_locidx_t local_id);
```
