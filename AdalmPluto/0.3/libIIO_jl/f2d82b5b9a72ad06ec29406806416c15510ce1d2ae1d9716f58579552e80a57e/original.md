```
C_iio_channel_attr_write_double(channel, attr, value)
```

Set the value of the given channel-specific attribute.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `attr::String` : a NULL-terminated string corresponding to the name of the attribute
  * `value::Float64` : A double value to set the attribute to

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gad9d6ec4a02948c6416cc99254bdbfa50)
