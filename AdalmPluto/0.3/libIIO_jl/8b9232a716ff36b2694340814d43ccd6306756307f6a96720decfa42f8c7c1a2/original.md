```
C_iio_buffer_get_poll_fd(buffer)
```

Get a pollable file descriptor.

Can be used to know when `iio_buffer_refill()` or `iio_buffer_push()` can be called

# Parameters

  * `buffer::Ptr{iio_buffer}` : A pointer to an iio_buffer structure

# Returns

  * On success, valid file descriptor
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga2ae96ee9f0748e55dfad996d6e9883f2)
