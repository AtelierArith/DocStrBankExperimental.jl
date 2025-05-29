```
C_iio_channel_attr_write_all()
```

THIS IS A PLACEHOLDER. THE DOCUMENTATION BELOW IS ONLY A COPY/PASTE OF THE C DOCUMENTATION.

Set the values of all channel-specific attributes.

# Parameters

  * chn : A pointer to an iio_channel structure
  * cb : A pointer to a callback function
  * data : A pointer that will be passed to the callback function

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

# NOTE

This function is especially useful when used with the network backend, as all the channel-specific attributes are written in one single command.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga6df693ee4f0c329d957f7c7ca3588f3f)
