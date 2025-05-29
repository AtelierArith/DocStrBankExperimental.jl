```
C_iio_device_get_buffer_attr(device, index)
```

Get the buffer-specific attribute present at the given index.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `index::UInt32`           : The index corresponding to the attribute

# Returns

  * On success, a NULL-terminated string.
  * On failure, if the assertions are enabled, throws an error.
  * On failure, if the assertions are disabled, returns an empty string.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga7225b9df06559012d549d627fb451c2a)
