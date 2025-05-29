```
C_iio_channel_attr_read(channel, attr)
```

Read the content of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute

# Returns

  * On success, `(nbytes, value::String)` where nbytes is the length of the value string.
  * On error, `(errno, "")` is returned, where errno is a negative error code.
  * If all the attributes are begin read, an array of the values above is returned.

The string may be shorter than the number of bytes returned as the conversion tirims excess null characters.

# NOTE

By passing NULL (replaced by an empty string in the Julia wrapper) as the "attr" argument to `iio_channel_attr_read`, it is now possible to read all of the attributes of a channel.

The buffer is filled with one block of data per attribute of the channel, by the order they appear in the iio_channel structure.

The first four bytes of one block correspond to a 32-bit signed value in network order. If negative, it corresponds to the errno code that were returned when reading the attribute; if positive, it corresponds to the length of the data read. In that case, the rest of the block contains the data.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga2c2ca5696d1341067051eb390d5014ae)
