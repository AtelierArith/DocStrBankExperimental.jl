```
gaspi_statistic_counter_get(counter, argument, value)
```

Get statistical counter.

### Parameters

  * `counter`: the counter to be retrieved.
  * `argument`: the argument for the counter.
  * `value`: Output paramter with the current value of the counter.

### Returns

GASPI_SUCCESS in case of SUCCESS, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_statistic_counter_get ( gaspi_statistic_counter_t counter, gaspi_number_t argument, unsigned long *value);
```
