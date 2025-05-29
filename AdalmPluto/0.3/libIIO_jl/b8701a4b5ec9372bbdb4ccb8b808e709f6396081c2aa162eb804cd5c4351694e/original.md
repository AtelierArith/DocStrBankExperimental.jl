```
C_iio_buffer_refill(buffer)
```

Fetch more samples from the hardware.

# Parameters

  * `buffer::Ptr{iio_buffer}` : A pointer to an iio_buffer structure

# Returns

  * On success, the number of bytes read is returned
  * On error, a negative errno code is returned

# NOTE

Only valid for input buffers

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gac999e5244b5a2cbbca5ecaef8303a4ff)
