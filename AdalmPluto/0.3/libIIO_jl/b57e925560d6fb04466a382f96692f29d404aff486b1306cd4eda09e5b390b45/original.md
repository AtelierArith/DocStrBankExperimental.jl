```
C_iio_device_find_attr(device, name)
```

Try to find a device-specific attribute by its name.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `name::String`            : A NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, a NULL-terminated string.
  * On failure, if the assertions are enabled, throws an error.
  * On failure, if the assertions are disabled, returns an empty string.

# NOTE

This function is useful to detect the presence of an attribute. It can also be used to retrieve the name of an attribute as a pointer to a static string from a dynamically allocated string.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gafcbece1ac6260b06bcdf02d9eb55e5fd)
