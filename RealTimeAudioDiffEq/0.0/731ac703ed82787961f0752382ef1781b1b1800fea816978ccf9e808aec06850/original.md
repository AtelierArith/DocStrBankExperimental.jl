```
start_DESource(source::DESource, output_device::PaDeviceIndex;
	sample_rate::Float64 = -1., 
	buffer_size::UInt32 = convert(UInt32, paFramesPerBufferUnspecified ))
```

Start a DESource with a given output device.

# Keyword arguments

  * `sample_rate::Float64 = -1.`: the sample rate of the stream. If negative, the default sample rate of the output device will be used.
  * `buffer_size::UInt32 = convert(UInt32, paFramesPerBufferUnspecified )`: the buffer size of the stream.
