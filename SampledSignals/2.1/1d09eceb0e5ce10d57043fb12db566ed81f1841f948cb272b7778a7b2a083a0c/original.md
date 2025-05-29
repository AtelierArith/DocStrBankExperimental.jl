Represents a sink that samples can be written to, such as an audio file or headphone output.

Subtypes should implement the `samplerate`, `nchannels`, `eltype`, and `unsafe_write` methods. `unsafe_write` can assume that the samplerate, channel count, and element type are all matching.
