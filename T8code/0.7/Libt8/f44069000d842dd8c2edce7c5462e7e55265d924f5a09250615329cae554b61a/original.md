```
t8_offset_range_send(start, _end, mpirank, offset_from, offset_to)
```

Count the number of processes in a given range [a,b] that send to a given other process in a repartitioning setting.

# Arguments

  * `start`:[in] The first mpi rank to be considered as sender.
  * `end`:[in] The last mpi rank to be considered as sender.
  * `mpirank`:[in] The mpirank to be considered as receiver.
  * `offset_from`:[in] The partition table of the current partition.
  * `offset_to`:[in] The partition table of the next partition.

# Returns

The number of processes p, such that *start* <= p <= *end* and p does send local trees (and possibly ghosts) to *mpirank*.

### Prototype

```c
int t8_offset_range_send (int start, int end, int mpirank, const t8_gloidx_t *offset_from, const t8_gloidx_t *offset_to);
```
