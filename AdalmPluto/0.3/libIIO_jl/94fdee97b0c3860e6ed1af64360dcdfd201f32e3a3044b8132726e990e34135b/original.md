```
C_iio_device_attr_read(device, attr)
```

Read the content of the given device-specific attribute.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `attr::String`            : A NULL-terminated string corresponding to the name of the attribute. Passing an empty string reads all the attributes.

# Returns

  * On success, the number of bytes written to the buffer and the attribute value as a `String`.
  * On error, a negative errno code is returned along an empty `String`.
  * If all the attributes are being read, an array of the values above is returned.

The string may be shorter than the number of bytes returned as the conversion trims excess null characters.

# NOTE

By passing NULL (replaced by an empty string in the Julia wrapper) as the "attr" argument to iio*device*attr_read, it is now possible to read all of the attributes of a device.

The buffer is filled with one block of data per attribute of the device, by the order they appear in the iio_device structure.

The first four bytes of one block correspond to a 32-bit signed value in network order. If negative, it corresponds to the errno code that were returned when reading the attribute; if positive, it corresponds to the length of the data read. In that case, the rest of the block contains the data.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaf0233eb0ef4a64ad70ebaef6328b0494)
