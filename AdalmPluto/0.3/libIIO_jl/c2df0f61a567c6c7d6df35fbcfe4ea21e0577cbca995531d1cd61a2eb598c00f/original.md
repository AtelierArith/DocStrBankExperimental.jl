```
C_iio_device_find_channel(device, name, isOutput)
```

Try to find a channel structure by its name of ID.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `name::String`            : A NULL-terminated string corresponding to the name or the ID of the channel to search for
  * `isOutput::Bool`          : True if the searched channel is output, False otherwise

# Returns

  * On success, a pointer to an iio_channel structure
  * On failure, if the assertions are enabled, throws an error.
  * On failure, if the assertions are disabled, returns NULL.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaffc6086189ba801ab5e95341d68f882b)
