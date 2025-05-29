```
C_iio_context_set_timeout(context, timeout_ms)
```

Set a timeout for I/O operations.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure
  * `timeout_ms::UInt32` : A positive integer representing the time in milliseconds after which a timeout occurs. A value of 0 is used to specify that no timeout should occur.

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gaba3f4c4f9f885f41a6c0b9ac79b7f28d)
