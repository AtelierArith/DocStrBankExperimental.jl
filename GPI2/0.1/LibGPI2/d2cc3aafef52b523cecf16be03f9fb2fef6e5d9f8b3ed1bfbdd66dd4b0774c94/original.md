```
gaspi_group_size(group, group_size)
```

Get the size of a given group. It returns the number of processes (ranks) in the group.

### Parameters

  * `group`: The group from which we want to know the size.
  * `group_size`: Output parameter with the group size.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_group_size (const gaspi_group_t group, gaspi_number_t * const group_size);
```
