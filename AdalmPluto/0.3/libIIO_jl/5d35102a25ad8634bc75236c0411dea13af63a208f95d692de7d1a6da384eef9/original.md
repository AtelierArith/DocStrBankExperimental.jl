```
C_iio_device_identify_filename(device, filename)
```

Identify the channel or debug attribute corresponding to a filename.

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `filename::String` : A NULL-terminated string corresponding to the filename

# Returns

  * On success, `(0, channel::Ptr{iio_channel}, attribute::String)` is returned.
  * On error, `(errno, NULL, "")` is returned, where errno is a negative error code.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Debug.html#ga87ef46fa578c7be7b3e2a6f9f16fdf7e)
