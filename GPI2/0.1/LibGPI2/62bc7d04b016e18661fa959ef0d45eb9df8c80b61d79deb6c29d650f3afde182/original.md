```
gaspi_proc_local_num(local_num)
```

Get the number of processes (ranks) started by the application.

### Parameters

  * `local_num`: The number of processes (ranks) in the same node

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_proc_local_num (gaspi_rank_t * const local_num);
```
