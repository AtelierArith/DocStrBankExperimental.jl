```
C_iio_device_get_channel(device, index)
```

Get the channel present at the given index.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `index::UInt32`           : The index corresponding to the channel

# Returns

  * On success, a pointer to an iio_channel structure
  * On failure, if the assertions are enabled, throws an error.
  * On failure, if the assertions are disabled, returns NULL.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga67289d735b7d8e1ed12ae0ea642bd1ac)
