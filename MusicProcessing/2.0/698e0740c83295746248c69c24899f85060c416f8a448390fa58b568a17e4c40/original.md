```
speedup(audio::SampleBuf, speed::Real, windowsize::Int = 1024, hopsize::Int = windowsize >> 2; kwargs...)
```

Returns a speedup audio waveform using various parameters

# Output

Return the speedup audio waveform as a SampleBuf{T, N} using windowsize and hopsize.

# Arguments

## `audio`

An audio of type SampleBuf{T, N} whose pitch is to be shifted.

## `windowsize`

A parameter used to define the window size for stft and istft functions.

## `hopsize`

A parameter used to define the number audio of frames between stft columns.

# Example

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)
audio_two_channel = SampleBuf(rand(10000, 2), 10)
audio_multi_channel = SampleBuf(rand(10000, 4), 10)

speedup(audio_one_channel, 2048, 512)
speedup(audio_one_channel, 2048, 512)
speedup(audio_one_channel, 2048, 512)

```
