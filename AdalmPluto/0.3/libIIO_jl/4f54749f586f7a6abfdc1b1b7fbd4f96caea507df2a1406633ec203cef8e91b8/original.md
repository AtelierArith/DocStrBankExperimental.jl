```
C_iio_channel_attr_get_filename(channel, attr)
```

Retrieve the filename of an attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, a NULL-terminated string
  * If the attribute name is unknown, NULL is returned. If the assertions are enabled, throws an error instead.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gab6462404bb6667e9e9241a18e09a1638)
