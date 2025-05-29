```
C_iio_channel_attr_write_bool(channel, attr, value)
```

Set the value of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute
  * `value::Bool` : A bool value to set the attribute to

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga9a385b9b05d20f33f8e587feb2ebe81a)
