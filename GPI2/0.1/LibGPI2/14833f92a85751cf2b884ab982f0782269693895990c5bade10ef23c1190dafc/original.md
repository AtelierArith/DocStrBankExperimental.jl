```
gaspi_error_str(error_code)
```

Get string describing return value. This is slightly more practical than [`gaspi_print_error`](@ref).

### Parameters

  * `error_code`: The return value to be described.

### Returns

A string that describes the return value.

### Prototype

```c
gaspi_string_t gaspi_error_str(gaspi_return_t error_code);
```
