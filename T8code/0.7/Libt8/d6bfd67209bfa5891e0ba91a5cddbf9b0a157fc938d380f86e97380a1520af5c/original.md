```
t8_offset_first(proc, offset)
```

Return the global id of the first local tree of a given process in a partition.

# Arguments

  * `proc`:[in] The rank of the process.
  * `offset`:[in] The partition table.

# Returns

The global id of the first local tree of *proc* in the partition *offset*.

### Prototype

```c
t8_gloidx_t t8_offset_first (const int proc, const t8_gloidx_t *offset);
```
