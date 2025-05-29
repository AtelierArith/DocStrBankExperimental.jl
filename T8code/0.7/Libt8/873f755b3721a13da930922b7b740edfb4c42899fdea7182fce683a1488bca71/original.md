```
t8_offset_in_range(tree_id, proc, offset)
```

Determine whether a given global tree id is a local tree of a given process in a certain partition.

# Arguments

  * `tree_id`:[in] A global tree id.
  * `proc`:[in] A mpi rank.
  * `offset`:[in] A partition table.

# Returns

nonzero if *tree_id* is a local tree of *proc* in *offset*. 0 if it is not.

### Prototype

```c
int t8_offset_in_range (const t8_gloidx_t tree_id, const int proc, const t8_gloidx_t *offset);
```
