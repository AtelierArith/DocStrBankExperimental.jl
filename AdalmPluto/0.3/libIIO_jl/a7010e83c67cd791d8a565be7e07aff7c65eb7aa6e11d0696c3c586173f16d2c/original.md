```
C_iio_device_create_buffer(device, samples_count, cyclic)
```

Create an input or output buffer associated to the given device.

# Parameters

  * `device::Ptr{iio_device}`: A pointer to an iio_device structure
  * `samples_count::UInt` : The number of samples that the buffer should contain
  * `cyclic::Bool` : If True, enable cyclic mode

# Returns

  * On success, a pointer to an iio_buffer structure
  * On error, if the assertions are enabled, throws an error.
  * On error, if the assertions are disabled, returns NULL.

# NOTE

Channels that have to be written to / read from must be enabled before creating the buffer.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gaea8067aca27b93a1260a0c563607a501)
