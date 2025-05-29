```
StreamInlet(info; max_buflen = 360, max_chunklen = 0, recover = True, procesing_flags = 0)
```

Establish a new stream inlet from a resolved stream description.

# Arguments

  * `info::StreamInfo`: A resolved stream description object (as coming from one of the                     resolver functions). Note: the stream*inlet may also be constructed                     with a fully-specified stream*info, if the desired channel format and                     count is already known up-front, but this is strongly discouraged and                     should only ever be done if there is no time to resolve the stream                     up-front (e.g., due to limitations in the client program).

# Keyword arguments

  * `max_buflen::Integer`: The maximum amount of data to buffer (in seconds if there is a                        nominal sampling rate, otherwise x100 in samples). Recording                        applications want to use a fairly large buffer size here, while                        real-time applications would only buffer as much as they need to                         perform their next calculation.
  * `max_chunklen::Integer`: The maximum size, in samples, at which chunks are transmitted                          (the default corresponds to the chunk sizes used by the sender).                          Recording programs can use a generous size here (leaving it to                          the network how to pack things), while real-time applications may                           want a finer (perhaps 1-sample) granularity. If left unspecified                          (=0), the sender determines the chunk granularity.
  * `recover::Bool`: Try to silently recover lost streams that are recoverable (those that                   have a source*id set). In all other cases (recover is false, or the                   stream is not recoverable), functions may throw a lost*error if the                   stream's source is lost (e.g., due to an app or computer crash).
