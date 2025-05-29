```
C_iio_channel_attr_read_double(channel, attr)
```

Read the content of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, `(0, value::Float64)` is returned
  * On error, `(errno, 0)` is returned, where errno is a negative error code. The second value should be discarded.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga75ac9b81eb7e7e8a961afb67748e4102)
