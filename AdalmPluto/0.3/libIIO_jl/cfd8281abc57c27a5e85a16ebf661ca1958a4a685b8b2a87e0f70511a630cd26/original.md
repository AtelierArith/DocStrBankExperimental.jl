```
C_iio_device_attr_write(device, attr, value)
```

Set the value of the given device-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute
  * `value::String`           : A NULL-terminated string to set the attribute to

# Returns

  * On success, the number of bytes written
  * On error, a negative errno code is returned

# NOTE

By passing NULL as the "attr" argument to `iio_device_attr_write`, it is now possible to write all of the attributes of a device.

The buffer must contain one block of data per attribute of the device, by the order they appear in the iio_device structure.

The first four bytes of one block correspond to a 32-bit signed value in network order. If negative, the attribute is not written; if positive, it corresponds to the length of the data to write. In that case, the rest of the block must contain the data.

# WARNING

If the value given is among the available values but not working on the radio, this function returns the success value without actually writing the value.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaaa2d1867c15ef8f8424164d0ccea4dd8)
