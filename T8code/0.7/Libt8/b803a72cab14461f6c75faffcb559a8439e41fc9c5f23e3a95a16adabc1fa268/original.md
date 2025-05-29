```
t8_offset_any_owner_of_tree(mpisize, gtree, offset)
```

Find any process that has a given tree as local tree.

# Arguments

  * `mpisize`:[in] The number of MPI ranks, also the number of entries in *offset* minus 1.
  * `gtree`:[in] The global id of a tree.
  * `offset`:[in] The partition to be considered.

# Returns

An MPI rank that has *gtree* as a local tree.

### Prototype

```c
int t8_offset_any_owner_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset);
```
