```
C_iio_channel_enable(channel)
```

Enable the given channel.

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure

# NOTE

Before creating an iio*buffer structure with `iio*device*create*buffer`, it is required to enable at least one channel of the device to read from.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga2b787983683d37966b5e1e5c6c121d6a)
