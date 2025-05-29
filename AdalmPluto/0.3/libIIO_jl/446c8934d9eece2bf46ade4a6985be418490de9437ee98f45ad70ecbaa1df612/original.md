```
C_iio_device_buffer_attr_write_all()
```

THIS IS A PLACEHOLDER. THE DOCUMENTATION BELOW IS ONLY A COPY/PASTE OF THE C DOCUMENTATION.

Set the values of all buffer-specific attributes.

# Parameters

  * dev : A pointer to an iio_device structure
  * cb : A pointer to a callback function
  * data : A pointer that will be passed to the callback function

# Returns

  * On success, 0 is returned
  * On error, a negative errno code is returned

# NOTE

This function is especially useful when used with the network backend, as all the buffer-specific attributes are written in one single command.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga3d77bb90c22eb1d0a13805bf69def068)
