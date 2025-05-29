```
t8_offset_nosend(proc, mpisize, offset_from, offset_to)
```

Query whether in a repartition setting a given process does send any of its local trees to any other process (including itself)

# Arguments

  * `proc`:[in] A mpi rank.
  * `mpisize`:[in] The number of MPI ranks, also the number of entries in *offset* minus 1.
  * `offset_from`:[in] The partition table of the current partition.
  * `offset_to`:[in] The partition table of the next partition.

# Returns

nonzero if *proc* will not send any local trees if we repartition from *offset_from* to *offset_to* 0 if it does send local trees.

### Prototype

```c
int t8_offset_nosend (int proc, int mpisize, const t8_gloidx_t *offset_from, const t8_gloidx_t *offset_to);
```
