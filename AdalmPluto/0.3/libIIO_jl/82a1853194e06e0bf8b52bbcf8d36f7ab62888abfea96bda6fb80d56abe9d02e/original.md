```
C_iio_channel_attr_write_raw(channel, attr, value)
```

Set the value of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute
  * `value::Ptr{Cvoid}`       : A pointer to the data to be written
  * `size::Csize_t`           : The number of bytes to be written

# Returns

  * On success, the number of bytes written
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gacd0d3dd36bdc64a9f967e21a891230eb)
