```
C_iio_channel_attr_write_longlong(channel, attr, value)
```

Set the value of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute
  * `value::Int64` : A long long value to set the attribute to

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gac55cb77a1baf797e54a8a4e31b2f4680)
