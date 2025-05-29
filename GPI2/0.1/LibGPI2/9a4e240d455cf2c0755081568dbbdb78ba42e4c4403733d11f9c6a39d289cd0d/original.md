```
gaspi_threads_get_num_cores(cores)
```

Get total number of available cpu cores

### Parameters

  * `cores`: Output paramter with the number of cores.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_threads_get_num_cores(gaspi_int * const cores) __attribute__ ((deprecated));
```
