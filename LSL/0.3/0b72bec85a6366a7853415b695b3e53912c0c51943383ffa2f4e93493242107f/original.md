```
StreamInfo
```

The StreamInfo type stores the declaration of a data stream.

Represents the following information:  a) stream data format (#channels, channel format)  b) core information (stream name, content type, sampling rate)  c) optional meta-data about the stream content (channel labels,      measurement units, etc.)

Whenever a program wants to provide a new stream on the lab network it will typically first create a StreamInfo to describe its properties and then construct a StreamOutlet with it to create the stream on the network. Recipients who discover the outlet can query the StreamInfo; it is also written to disk when recording the stream (playing a similar role as a file header).
