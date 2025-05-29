```
C_iio_buffer_cancel(buffer)
```

Cancel all buffer operations.

# Parameters

  * `buffer::Ptr{iio_buffer}` :The buffer for which operations should be canceled

This function cancels all outstanding buffer operations previously scheduled. This means any pending `iio_buffer_push()` or `iio_buffer_refill()` operation will abort and return immediately, any further invocations of these functions on the same buffer will return immediately with an error.

Usually `iio_buffer_push()` and `iio_buffer_refill()` will block until either all data has been transferred or a timeout occurs. This can depending on the configuration take a significant amount of time. `iio_buffer_cancel()` is useful to bypass these conditions if the buffer operation is supposed to be stopped in response to an external event (e.g. user input).

To be able to capture additional data after calling this function the buffer should be destroyed and then re-created.

This function can be called multiple times for the same buffer, but all but the first invocation will be without additional effect.

This function is thread-safe, but not signal-safe, i.e. it must not be called from a signal handler.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga0e42431688750313cfa077ab4f6e0282)
