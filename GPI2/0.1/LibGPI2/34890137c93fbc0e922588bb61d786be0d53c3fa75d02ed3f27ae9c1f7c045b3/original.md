```
gaspi_proc_num(proc_num)
```

Get the number of processes (ranks) started by the application.

### Parameters

  * `proc_num`: The number of processes (ranks) started by the application.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_proc_num (gaspi_rank_t * const proc_num);
```
