```
gaspi_group_ranks(group, group_ranks)
```

Get the list of ranks forming a given group.

### Parameters

  * `group`: The group we are interested in.
  * `group_ranks`: Output parameter: an array with the ranks belonging to the given group.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_group_ranks (const gaspi_group_t group, gaspi_rank_t * const group_ranks);
```
