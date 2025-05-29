```
C_iio_buffer_first(buffer, channel)
```

Find the first sample of a channel in a buffer.

# Parameters

  * `buffer::Ptr{iio_buffer}` : A pointer to an iio_buffer structure
  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure

# Returns

  * A pointer to the first sample found, or to the end of the buffer if no sample for the given channel is present in the buffer

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga000d2f4c8b72060db1c38ec905bf4156)
