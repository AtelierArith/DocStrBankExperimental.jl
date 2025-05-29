```
slowdown(audio::SampleBuf, ratio::Real, windowsize::Int = 1024, hopsize::Int = windowsize >> 2; kwargs...)
```

Returns a slowdowned audio using various parameters

# Output

Return the slowdowned audio waveform as a SampleBuf{T, N} using windowsize and hopsize.

# Arguments

## `audio`

An audio of type SampleBuf{T, N} whose speed is to be slowdowned.

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

slowdown(audio_one_channel, 2048, 512)
slowdown(audio_two_channel, 2048, 512)
slowdown(audio_multi_channel, 2048, 512)

```
