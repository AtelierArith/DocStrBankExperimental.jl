```
t8_offset_last_owner_of_tree(mpisize, gtree, offset, some_owner)
```

Find the biggest process that has a given tree as local tree. To increase the runtime, an arbitrary process having this tree as local tree can be passed as an argument. Otherwise, such an owner is computed during the call.

# Arguments

  * `mpisize`:[in] The number of MPI ranks, also the number of entries in *offset* minus 1.
  * `gtree`:[in] The global id of a tree.
  * `offset`:[in] The partition to be considered.
  * `some_owner`:[in,out] If >= 0 considered as input: a process that has *gtree* as local tree. If < 0 on output a process that has *gtree* as local tree. Specifying *some_owner* increases the runtime from O(log mpisize) to O(n), where n is the number of owners of the tree.

# Returns

The biggest rank that has *gtree* as a local tree.

### Prototype

```c
int t8_offset_last_owner_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, int *some_owner);
```
