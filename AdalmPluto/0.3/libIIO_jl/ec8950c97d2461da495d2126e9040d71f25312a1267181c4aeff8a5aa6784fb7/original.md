```
C_iio_channel_get_attr(channel, index)
```

Get the channel-specific attribute present at the given index.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `index::UInt32` : The index corresponding to the attribute

# Returns

  * On success, a NULL-terminated string.
  * On failure, if the assertions are enabled, throws an error.
  * On failure, if the assertions are disabled, returns an empty string.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gafc3c52f360424c097a24d1925923d772)
