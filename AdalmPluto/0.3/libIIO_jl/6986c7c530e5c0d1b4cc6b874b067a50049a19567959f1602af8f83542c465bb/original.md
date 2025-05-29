```
C_iio_device_buffer_attr_read_double(device, attr)
```

Read the content of the given buffer-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, (0, value::Float64) is returned.
  * On error, (errno, value::Float64) is returned, where errno is a negative error code. `value` should be discarded.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga44952198b73ff6b0c0c0b53d3cd6d1bd)
