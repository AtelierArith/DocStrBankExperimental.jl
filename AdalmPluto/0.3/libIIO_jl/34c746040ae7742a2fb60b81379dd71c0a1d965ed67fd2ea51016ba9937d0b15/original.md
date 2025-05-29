```
C_iio_channel_attr_write(channel, attr, value)
```

Set the value of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute
  * `value::String` : A NULL-terminated string to set the attribute to

# Returns

  * On success, the number of bytes written
  * On error, a negative errno code is returned

# NOTE

By passing NULL as the "attr" argument to `iio_channel_attr_write`, it is now possible to write all of the attributes of a channel.

The buffer must contain one block of data per attribute of the channel, by the order they appear in the iio_channel structure.

The first four bytes of one block correspond to a 32-bit signed value in network order. If negative, the attribute is not written; if positive, it corresponds to the length of the data to write. In that case, the rest of the block must contain the data.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga35c76ce5fcae4c551b7c78d648665a41)
