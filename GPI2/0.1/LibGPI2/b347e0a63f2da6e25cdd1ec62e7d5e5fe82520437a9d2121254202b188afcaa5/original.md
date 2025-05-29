```
gaspi_proc_term(timeout_ms)
```

Shutdown procedure. It is a synchronous local time-based blocking operation that releases resources and performs the required clean-up.

### Parameters

  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_proc_term (const gaspi_timeout_t timeout_ms);
```
