```
C_iio_channel_read!(chn, buf, dst)
```

Demultiplex and convert the samples of a given channel.

# Parameters

  * `chn::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `buf::Ptr{iio_buffer}` : A pointer to an iio_buffer structure
  * `dst::Array{UInt8}` : An array where the converted data will be stored

# Returns

  * The size of the converted data written is dst, in bytes

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga5c01edc37b0b57aef503abd5989a6a30)
