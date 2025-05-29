```
C_iio_device_attr_read_bool(device, attr)
```

Read the content of the given device-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, `(0, value::Bool)` is returned.
  * On error, `(errno, value::Bool)` is returned, where errno is a negative error code. `value` should be discarded.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga96364b7c7097bb8e4656924ea896a502)
