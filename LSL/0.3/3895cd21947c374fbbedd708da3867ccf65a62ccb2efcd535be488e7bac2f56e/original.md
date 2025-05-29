```
StreamOutlet(info; chunk_size = 0, max_buffered = 360)
```

Establish a new stream outlet. This makes the stream discoverable.

# arguments

  * `info::StreamInfo`: The stream information to use for creating this stream. Stays constant                     over the lifetime of the outlet.

# Keyword arguments

  * `chunk_size::Integer`: Desired chunk granularity (in samples) for transmission. If                        specified as 0, each push operation yields one chunk. Stream                        recipients can have this setting bypassed.
  * `max_buffered::Integer`: Maximum amount of data to buffer (in seconds if there is a                          nominal sampling rate, otherwise x100 in samples). A good default                          is 360, which corresponds to 6 minutes of data. Note that, for                          high-bandwidth data you will almost certainly want to use a lower                          value here to avoid running out of RAM.
