```
C_iio_device_get_name(device)
```

Retrieve the device name (e.g. xadc)

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure

# Returns

  * A NULL-terminated string

# NOTE

If the device has no name and the assertions are enabled, throws an error. If the device has no name and the assertions are enabled, returns an emtpy string.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga711666b3b3b6314fbe7e592b4632ab85)
