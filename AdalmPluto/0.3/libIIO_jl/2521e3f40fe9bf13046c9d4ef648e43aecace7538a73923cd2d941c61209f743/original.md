```
C_iio_channel_attr_read_all()
```

THIS IS A PLACEHOLDER. THE DOCUMENTATION BELOW IS ONLY A COPY/PASTE OF THE C DOCUMENTATION.

Read the content of all channel-specific attributes.

# Parameters

  * chn : A pointer to an iio_channel structure
  * cb : A pointer to a callback function
  * data : A pointer that will be passed to the callback function

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

# NOTE

This function is especially useful when used with the network backend, as all the channel-specific attributes are read in one single command.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gab9c28b0cd94c0607bcc7cac16219eb48)
