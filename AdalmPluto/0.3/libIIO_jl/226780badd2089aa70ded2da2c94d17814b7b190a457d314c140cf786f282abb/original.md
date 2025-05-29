```
C_iio_device_attr_write_bool(device, attr, value)
```

Set the value of the given device-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute
  * `value::Bool`             : A bool value to set the attribute to

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga9f53f9d1c3dc9f87191943fcbd1a7324)
