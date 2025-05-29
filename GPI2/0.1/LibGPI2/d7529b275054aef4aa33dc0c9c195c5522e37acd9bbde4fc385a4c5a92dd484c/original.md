```
gaspi_passive_transfer_size_max(passive_transfer_size_max)
```

Get the maximum allowed size (in bytes) allowed in passive communication.

### Parameters

  * `passive_transfer_size_max`: Output parameter with the maximum allowed size (in bytes) for passive communication.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_passive_transfer_size_max (gaspi_size_t * const passive_transfer_size_max);
```
