```
C_iio_buffer_foreach_sample()
```

THIS IS A PLACEHOLDER. THE DOCUMENTATION BELOW IS ONLY A COPY/PASTE OF THE C DOCUMENTATION.

Call the supplied callback for each sample found in a buffer.

# Parameters

  * buf : A pointer to an iio_buffer structure
  * callback : A pointer to a function to call for each sample found
  * data : A user-specified pointer that will be passed to the callback

# Returns

  * number of bytes processed.

# NOTE

The callback receives four arguments:

  * A pointer to the iio_channel structure corresponding to the sample,
  * A pointer to the sample itself,
  * The length of the sample in bytes,
  * The user-specified pointer passed to `iio_buffer_foreach_sample`.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga810ec50155e82331b18ec71d3c507104)
