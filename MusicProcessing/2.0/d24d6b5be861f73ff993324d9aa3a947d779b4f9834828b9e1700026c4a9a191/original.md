```
zero_crossing_rate(audio::SampleBuf{T, 1}, framesize::Int = 1024, hopsize::Int = framesize >> 2)
```

Returns zero crossing rate in a audio waveform

# Output

Returns a array of zero-crossings in y along the selected axis of audio using various parameters

# Arguments

## `audio`

An audio of type SampleBuf{T, N} whose speed is to be slowdowned.

## `framesize`

A parameter used to define the framesize to calculate no of zero crossings.

## `hopsize`

A parameter used to define the number audio of frames between frames size columns.

# Example

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)

zero_crossing_rate(audio_one_channel, 2048, 512)
```
