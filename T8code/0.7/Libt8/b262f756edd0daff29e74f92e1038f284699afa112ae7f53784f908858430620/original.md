```
t8_forest_partition_next_nonempty_rank(forest, rank)
```

If t8*forest*partition*create*offsets was already called, compute for a given rank the next greater rank that is not empty.

# Arguments

  * `forest`:[in] The forest.
  * `rank`:[in] An MPI rank.

# Returns

A rank q > *rank* such that the forest has elements on *q*. If such a *q* does not exist, returns mpisize.

### Prototype

```c
int t8_forest_partition_next_nonempty_rank (t8_forest_t forest, int rank);
```
