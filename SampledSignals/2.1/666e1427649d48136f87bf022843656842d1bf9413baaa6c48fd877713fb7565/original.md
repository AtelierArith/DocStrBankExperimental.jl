Represents a source of samples, such as an audio file, microphone input, or SDR Receiver.

Subtypes should implement the `samplerate`, `nchannels`, `eltype`, and `unsafe_read!` methods. `unsafe_read!` can assume that the samplerate, channel count, and element type are all matching.
