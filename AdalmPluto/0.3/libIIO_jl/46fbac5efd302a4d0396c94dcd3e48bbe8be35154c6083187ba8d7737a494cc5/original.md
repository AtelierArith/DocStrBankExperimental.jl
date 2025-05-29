```
C_iio_device_buffer_attr_write_longlong(device, attr, value)
```

Set the value of the given buffer-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute
  * `value::Int64`            : A long long value to set the attribute to

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gac05869aa707121328dd72cdad10cedf2)
