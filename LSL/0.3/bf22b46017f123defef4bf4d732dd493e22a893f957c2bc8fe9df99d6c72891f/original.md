```
channel_format(info::StreamInfo)
```

Return (Julia) channel format of the stream `info`.

All channels in a stream have the same format. However, a device might offer multiple time-synched streams each with its own format.

Note that the format is returned from the parametric type of the StreamInfo object, it is not queried from the library.
