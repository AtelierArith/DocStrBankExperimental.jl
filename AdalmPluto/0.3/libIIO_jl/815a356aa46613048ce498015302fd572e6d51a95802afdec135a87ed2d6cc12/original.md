```
C_iio_buffer_push(buffer)
```

Send the samples to the hardware.

# Parameters

  * `buffer::Ptr{iio_buffer}` : A pointer to an iio_buffer structure

# Returns

  * On success, the number of bytes written is returned
  * On error, a negative errno code is returned

# NOTE

Only valid for output buffers

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gae7033c625d128667a56cf482aa3149bd)
