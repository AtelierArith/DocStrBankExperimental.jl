```
t8_offset_all_owners_of_tree(mpisize, gtree, offset, owners)
```

Compute a list of all processes that own a specific tree.n *offset* minus 1.

# Arguments

  * `mpisize`:[in] The number of MPI ranks, also the number of entries in *offset* minus 1.
  * `gtree`:[in] The global index of a tree.
  * `offset`:[in] The partition to be considered.
  * `owners`:[in,out] On input an initialized [`sc_array`](@ref) with integer entries and zero elements. On output a sorted list of all MPI ranks that have *gtree* as a local tree in *offset*.

### Prototype

```c
void t8_offset_all_owners_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, sc_array_t *owners);
```
