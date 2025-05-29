```
gaspi_numa_socket(socket)
```

Get NUMA socket

### Parameters

  * `socket`: Output parameter with the socket

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case GPI2 was not started with NUMA enabled.

### Prototype

```c
gaspi_return_t gaspi_numa_socket(gaspi_uchar * const socket);
```
