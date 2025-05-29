```
gaspi_allreduce_elem_max(elem_max)
```

Get the maximum number of elements allowed in [`gaspi_allreduce`](@ref).

### Parameters

  * `elem_max`: Output parameter with the maximum number of elements.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_allreduce_elem_max (gaspi_number_t * const elem_max);
```
