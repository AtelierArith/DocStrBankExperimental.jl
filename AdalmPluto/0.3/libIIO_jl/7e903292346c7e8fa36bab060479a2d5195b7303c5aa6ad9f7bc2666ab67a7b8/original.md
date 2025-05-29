```
C_iio_buffer_push_partial(buffer, sample_count)
```

Send a given number of samples to the hardware.

# Parameters

  * `buffer::Ptr{iio_buffer}` : A pointer to an iio_buffer structure
  * `samples_count::UInt` : The number of samples to submit

# Returns

  * On success, the number of bytes written is returned
  * On error, a negative errno code is returned

# NOTE

Only valid for output buffers

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga367b7368532aebb35a0d56bccc550570)
