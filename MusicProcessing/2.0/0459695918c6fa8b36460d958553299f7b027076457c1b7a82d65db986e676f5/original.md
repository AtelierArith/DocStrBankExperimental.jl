```
resample(audio::SampleBuf{T, 2}, samplerate::Real)
```

Resamples input audio with a provided sample rate

# Output

Return the resampled audio as a SampleBuf{T, 2} with given sample rate.

# Arguments

## `audio`

An audio of type SampleBuf{T, 2} which is to be resampled.

## `samplerate`

A parameter to specify the samplerate for final output's sample rate

# Example

```julia
using MusicProcessing

audio_two_channel = SampleBuf(rand(1000, 2), 10)

resample(audio_two_channel, 5)
```
