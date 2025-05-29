```
t8_offset_prev_owner_of_tree(mpisize, gtree, offset, current_owner)
```

Given a process current_owner that has the tree gtree as local tree, find the next smaller rank that also has this tree as local tree.

# Arguments

  * `mpisize`:[in] The number of MPI ranks, also the number of entries in *offset* minus 1.
  * `gtree`:[in] The global id of a tree.
  * `offset`:[in] The partition to be considered.
  * `current_owner`:[in] A process that has *gtree* as local tree.

# Returns

The MPI rank of the next smaller rank than *current_owner* that has *gtree* as local tree. -1 if non such rank exists.

### Prototype

```c
int t8_offset_prev_owner_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, const int current_owner);
```
