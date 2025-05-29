```
Channel(dev::AbstractDeviceOrTrigger, channel::Ptr{iio_channel})
```

Initializes a new instance of the Channel type.

# Parameters

  * `dev::AbstractDeviceOrTrigger` : The parent device handle (`Device` or `Trigger`)
  * `channel::Ptr{iio_channel}` :  A valid pointer to an IIO channel.

# Returns

  * A new instance of this type
