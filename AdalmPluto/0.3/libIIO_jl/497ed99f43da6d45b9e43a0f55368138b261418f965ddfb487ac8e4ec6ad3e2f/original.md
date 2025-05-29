```
C_iio_device_get_sample_size(device)
```

Get the current sample size.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure

# Returns

  * On success, the sample size in bytes
  * On error, a negative errno code is returned

# NOTE

The sample size is not constant and will change when channels get enabled or disabled.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Debug.html#ga52b3e955c10d6f962b2c2e749c7c02fb)
