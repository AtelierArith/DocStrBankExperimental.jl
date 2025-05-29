```
C_iio_device_get_trigger(device)
```

Retrieve the trigger of a given device.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure

# Returns

  * On success, `(0, trigger::Ptr{iio_device})` is returned.
  * On error, `(errno, NULL)` is returned, where errno is a negative error code.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gae3ce1d7385ca02a9f6c36768fa41c610)
