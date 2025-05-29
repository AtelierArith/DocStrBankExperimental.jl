```
C_iio_channel_attr_read_bool(channel, attr)
```

Read the content of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, `(0, value::Bool)` is returned
  * On error, `(errno, false)` is returned, where errno is a negative error code. The second value should be discarded.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga319f39c313bbd4d331e23df51e4d3ce6)
