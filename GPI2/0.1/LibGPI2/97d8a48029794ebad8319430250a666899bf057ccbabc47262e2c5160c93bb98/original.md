```
gaspi_proc_init(timeout_ms)
```

Initialization procedure to start GPI-2. It is a non-local synchronous time-based blocking procedure.

### Parameters

  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_proc_init (const gaspi_timeout_t timeout_ms);
```
