```
gaspi_atomic_max(max_value)
```

Maximum value an [`gaspi_atomic_value_t`](@ref) can hold.

### Parameters

  * `max_value`: Output parameter with the maximum value allowed for atomic operations.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_atomic_max(gaspi_atomic_value_t *max_value);
```
