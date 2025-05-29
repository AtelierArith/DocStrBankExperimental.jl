```
desc(info::StreamInfo)
```

Get extended description of the stream as an XMLElement.

It is highly recommended that at least the channel labels are described here. See code examples on the LSL wiki. Other information, such as amplifier settings, measurement units if deviating from defaults, setup information, subject information, etc., can be specified here, as well. Meta-data recommendations follow the XDF file format project (github.com/sccn/xdf/wiki/Meta-Data or web search for: XDF meta-data).

Important: if you use a stream content type for which meta-data recommendations exist, please  try to lay out your meta-data in agreement with these recommendations for compatibility with other applications.
