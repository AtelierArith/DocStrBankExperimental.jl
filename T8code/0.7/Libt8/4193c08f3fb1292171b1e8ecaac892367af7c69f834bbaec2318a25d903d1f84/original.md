```
t8_offset_empty(proc, offset)
```

Check whether a given process has no local trees in a given partition.

# Arguments

  * `proc`:[in] A mpi rank.
  * `offset`:[in] A partition table.

# Returns

nonzero if *proc* does not have local trees in *offset*. 0 otherwise.

### Prototype

```c
int t8_offset_empty (const int proc, const t8_gloidx_t *offset);
```
