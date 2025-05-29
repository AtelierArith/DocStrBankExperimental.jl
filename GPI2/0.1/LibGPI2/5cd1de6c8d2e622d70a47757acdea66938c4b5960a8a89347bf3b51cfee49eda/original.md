```
gaspi_proc_local_rank(local_rank)
```

Get the process local rank.

### Parameters

  * `local_rank`: Rank within a node of calling process.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_proc_local_rank (gaspi_rank_t * const local_rank);
```
