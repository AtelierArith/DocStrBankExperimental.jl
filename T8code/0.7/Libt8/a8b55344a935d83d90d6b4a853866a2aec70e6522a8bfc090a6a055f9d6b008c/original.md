```
t8_cmesh_ltreeid_to_ghostid(cmesh, ltreeid)
```

Given a local tree id that belongs to a ghost, return the index of the ghost.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `ltreeid`:[in] The local id of a ghost, satisfying t8*cmesh*treeid*is*ghost, thus num_trees <= *ltreeid* < num_trees + num_ghosts

# Returns

The index of the ghost within all ghosts, thus an index 0 <= index < num_ghosts *cmesh* must be committed before calling this function.

### Prototype

```c
t8_locidx_t t8_cmesh_ltreeid_to_ghostid (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid);
```
