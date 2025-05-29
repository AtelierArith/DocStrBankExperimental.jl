```
mono(audio::SampleBuf{T, N})
```

Converts a multichannel audio to single channel

# Output

Return the mono channel audio as a SampleBuf{T, 1} with initial sample rate.

# Arguments

## `audio`

An audio of type SampleBuf{T, N} which is to be converted to single channel audio.

# Example

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(1000), 10)
audio_two_channel = SampleBuf(rand(1000, 2), 10)
audio_multi_channel = SampleBuf(rand(1000, 4), 10)

mono(audio_one_channel)
mono(audio_two_channel)
mono(audio_multi_channel)
```
