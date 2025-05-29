```
gaspi_threads_run(_function, arg)
```

Run a particular task (function)

### Parameters

  * `function`: The function to run.
  * `arg`: The arguments of the function to run.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_threads_run(void* (*function)(void*), void *arg) __attribute__ ((deprecated));
```
