```
gaspi_allreduce_buf_size(buf_size)
```

Get the internal buffer size for [`gaspi_allreduce_user`](@ref).

### Parameters

  * `buf_size`: Output parameter with the buffer size.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_allreduce_buf_size (gaspi_size_t * const buf_size);
```
