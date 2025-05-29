```
t8_offset_last(proc, offset)
```

Return the last local tree of a given process in a partition.

# Arguments

  * `proc`:[in] A mpi rank.
  * `offset`:[in] A partition table.

# Returns

The global tree id of the last local tree of *proc* in *offset*.

### Prototype

```c
t8_gloidx_t t8_offset_last (const int proc, const t8_gloidx_t *offset);
```
