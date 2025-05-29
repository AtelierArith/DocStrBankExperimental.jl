```
C_iio_buffer_set_blocking_mode(buffer, blocking)
```

Make `iio_buffer_refill()` and `iio_buffer_push()` blocking or not.

After this function has been called with blocking == false, `iio_buffer_refill()` and `iio_buffer_push()` will return -EAGAIN if no data is ready. A device is blocking by default.

# Parameters

  * `buffer::Ptr{iio_buffer}` : A pointer to an iio_buffer structure
  * `blocking::Bool` : true if the buffer API should be blocking, else false

# Returns

  * On success, 0
  * On error, a negative errno code is returned

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gadf834d825ece149886283bcb8c2a5466)
