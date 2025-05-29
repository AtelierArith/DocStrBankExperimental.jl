```
C_iio_device_buffer_attr_read_longlong(device, attr)
```

Read the content of the given buffer-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, (0, value::Int64) is returned.
  * On error, (errno, value::Int64) is returned, where errno is a negative error code. `value` should be discarded.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gae5b9be890edb372d3e30a14ce1c79874)
