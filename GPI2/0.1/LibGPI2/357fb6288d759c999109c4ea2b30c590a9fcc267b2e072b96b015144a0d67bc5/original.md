```
gaspi_group_add(group, rank)
```

Add a given rank to a group.

### Parameters

  * `group`: Group to add.
  * `rank`: Rank to add to the group.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_group_add (const gaspi_group_t group, const gaspi_rank_t rank);
```
