```
C_iio_channel_get_name(channel)
```

Retrieve the channel name (e.g. vccint)

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure

# Returns

  * A NULL-terminated string.

# NOTE

If the channel has no name, and the assertions are enabled, throws an error. If the assertions are disabled, returns an empty string.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga37346a6f3fcfb1eb40572aec6c3b39ac)
