```
C_iio_device_buffer_attr_read(device, attr)
```

Read the content of the given buffer-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute. Passing an empty string reads all the attributes.

# Returns

  * On success, (number*of*bytes, value::String) is returned, where number of bytes should be the length of the string.
  * On error, (errno, "") is returned, where errno is a negative error code.
  * If all the attributes are being read, an array of the values above is returned.

The string may be shorter than the actual number of bytes returned as the conversion trims excess null characters.

# NOTE

By passing NULL (replaced by an empty string in the Julia wrapper) as the "attr" argument to `iio_device_buffer_attr_read`, it is now possible to read all of the attributes of a device.

The buffer is filled with one block of data per attribute of the buffer, by the order they appear in the iio_device structure.

The first four bytes of one block correspond to a 32-bit signed value in network order. If negative, it corresponds to the errno code that were returned when reading the attribute; if positive, it corresponds to the length of the data read. In that case, the rest of the block contains the data.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaa77d52bb9dea248cc3de682778a08a6f)
