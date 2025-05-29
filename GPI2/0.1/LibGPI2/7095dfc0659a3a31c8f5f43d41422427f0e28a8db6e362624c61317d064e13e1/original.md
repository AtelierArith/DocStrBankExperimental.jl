```
gaspi_threads_init_user(use_nr_of_threads)
```

Initialize threads (a particular number of threads)

### Parameters

  * `use_nr_of_threads`: Number of threads to start.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_threads_init_user(const unsigned int use_nr_of_threads) __attribute__ ((deprecated));
```
