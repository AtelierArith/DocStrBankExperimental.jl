```
C_iio_device_set_trigger(device, trigger)
```

Associate a trigger to a given device.

# Parameters

  * `device::Ptr{iio_device}`  : A pointer to an iio_device structure
  * `trigger::Ptr{iio_device}` : a pointer to the iio_device structure corresponding to the trigger that should be associated.

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga3b8d1e621357f0755925d98555f53d9a)
