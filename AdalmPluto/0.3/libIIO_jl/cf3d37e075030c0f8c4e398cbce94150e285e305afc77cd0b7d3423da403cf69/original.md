```
C_iio_channel_find_attr(channel, name)
```

Try to find a channel-specific attribute by its name.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `name::String` : A NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, a NULL-terminated string.
  * On failure, if the assertions are enabled, throws an error.
  * On failure, if the assertions are disabled, returns an empty string.

# NOTE

This function is useful to detect the presence of an attribute. It can also be used to retrieve the name of an attribute as a pointer to a static string from a dynamically allocated string.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga13b2db3252a2380a2b0b1bb15b8034a4)
