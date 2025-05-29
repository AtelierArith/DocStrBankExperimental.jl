```
gaspi_transfer_size_max(transfer_size_max)
```

Get the maximum size (in bytes) that can be communicated in a single request (read, write, etc.).

### Parameters

  * `transfer_size_max`: Output parameter with the maximum transfer size.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_transfer_size_max (gaspi_size_t * const transfer_size_max);
```
