```
gaspi_statistic_counter_info(counter, counter_argument, counter_name, counter_description, verbosity_level)
```

Get information about a counter.

### Parameters

  * `counter`: the counter.
  * `counter_argument`: Output parameter with meaning of the counter.
  * `counter_name`: Output parameter with the name of the counter.
  * `counter_description`: Output parameter with a more detailed description of the counter.
  * `verbosity_level`: Output parameter with the minumum verbosity level to activate the counter.

### Returns

GASPI_SUCCESS in case of SUCCESS, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_statistic_counter_info( gaspi_statistic_counter_t counter, gaspi_statistic_argument_t* counter_argument, gaspi_string_t* counter_name, gaspi_string_t* counter_description, gaspi_number_t* verbosity_level);
```
