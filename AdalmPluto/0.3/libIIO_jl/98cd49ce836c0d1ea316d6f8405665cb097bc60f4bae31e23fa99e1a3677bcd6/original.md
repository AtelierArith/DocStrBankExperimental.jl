```
C_iio_device_buffer_attr_read_all()
```

THIS IS A PLACEHOLDER. THE DOCUMENTATION BELOW IS ONLY A COPY/PASTE OF THE C DOCUMENTATION.

Read the content of all buffer-specific attributes.

# Parameters

  * dev : A pointer to an iio_device structure
  * cb : A pointer to a callback function
  * data : A pointer that will be passed to the callback function

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

# NOTE

This function is especially useful when used with the network backend, as all the buffer-specific attributes are read in one single command.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaae5bf33ad1bd1b14155eab4a018c576c)
