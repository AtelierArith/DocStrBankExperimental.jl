```
t8_offset_next_nonempty_rank(rank, mpisize, offset)
```

Find the next higher rank that is not empty. returns mpisize if this rank does not exist.

# Arguments

  * `proc`:[in] An MPI rank.
  * `mpisize`:[in] The number of total MPI ranks.
  * `offset`:[in] An array with at least *mpisize* + 1 entries.

# Returns

A rank *p* such that *p* > *rank* and [`t8_offset_empty`](@ref) (*p*, *offset*) is True and [`t8_offset_empty`](@ref) (*q*, *offset*) is False for all *rank* < *q* < *p*. If no such *q* exists, *mpisize* is returned.

### Prototype

```c
int t8_offset_next_nonempty_rank (const int rank, const int mpisize, const t8_gloidx_t *offset);
```
