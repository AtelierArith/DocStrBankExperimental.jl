```
C_iio_device_set_kernel_buffers_count(device, nb_buffers)
```

Configure the number of kernel buffers for a device.

This function allows to change the number of buffers on kernel side.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `nb_buffers::UInt32`      : The number of buffers

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga8ad2357c4caf7afc778060a08e6e2209)
