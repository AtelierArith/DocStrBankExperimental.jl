```
gaspi_transfer_size_min(transfer_size_min)
```

Get the minimum size (in bytes) that can be communicated in a single request (write, read, etc.)

### Parameters

  * `transfer_size_min`: Output parameter with the minimum size that be transfered.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_transfer_size_min (gaspi_size_t * const transfer_size_min);
```
