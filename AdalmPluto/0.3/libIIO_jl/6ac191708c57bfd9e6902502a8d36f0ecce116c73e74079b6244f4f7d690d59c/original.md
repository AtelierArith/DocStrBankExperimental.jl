```
C_iio_device_attr_write_raw(device, attr, value)
```

Set the value of the given device-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute
  * `value::Ptr{Cvoid}`       : A pointer to the data to be written
  * `size::Csize_t`           : The number of bytes to be written

# Returns

  * On success, the number of bytes written
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga30829a67dcdffc902c4ba6801233e79a)
