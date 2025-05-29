```
gaspi_passive_transfer_size_min(passive_transfer_size_min)
```

Get the minimum allowed size (in bytes) allowed in passive communication.

### Parameters

  * `passive_transfer_size_min`: Output parameter with the minimum allowed size (in bytes) for passive communication.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_passive_transfer_size_min (gaspi_size_t * const passive_transfer_size_min);
```
