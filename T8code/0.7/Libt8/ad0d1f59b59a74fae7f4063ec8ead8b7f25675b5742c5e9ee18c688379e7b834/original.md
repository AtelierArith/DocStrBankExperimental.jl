```
t8_offset_num_trees(proc, offset)
```

The number of trees of a given process in a partition.

# Arguments

  * `proc`:[in] A mpi rank.
  * `offset`:[in] A partition table.

# Returns

The number of local trees of *proc* in the partition *offset*.

### Prototype

```c
t8_gloidx_t t8_offset_num_trees (const int proc, const t8_gloidx_t *offset);
```
