```
t8_offset_any_owner_of_tree_ext(mpisize, start_proc, gtree, offset)
```

Find any process that has a given tree as local tree.

# Arguments

  * `mpisize`:[in] The number of MPI ranks, also the number of entries in *offset* minus 1.
  * `start_proc`:[in] The mpirank to start the search with.
  * `gtree`:[in] The global id of a tree.
  * `offset`:[in] The partition to be considered.

# Returns

An MPI rank that has *gtree* as a local tree.

### Prototype

```c
int t8_offset_any_owner_of_tree_ext (const int mpisize, const int start_proc, const t8_gloidx_t gtree, const t8_gloidx_t *offset);
```
