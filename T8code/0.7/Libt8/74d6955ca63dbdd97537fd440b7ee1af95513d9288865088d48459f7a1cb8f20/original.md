```
t8_cmesh_get_ghost_class(cmesh, lghost_id)
```

Return the eclass of a given local ghost. TODO: Should we refer to indices or consequently use cghost_t?

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `ghost_id`:[in] The local id of the ghost whose eclass will be returned. 0 <= *tree_id* < cmesh.num_ghosts.

# Returns

The eclass of the given ghost. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_eclass_t t8_cmesh_get_ghost_class (t8_cmesh_t cmesh, t8_locidx_t lghost_id);
```
