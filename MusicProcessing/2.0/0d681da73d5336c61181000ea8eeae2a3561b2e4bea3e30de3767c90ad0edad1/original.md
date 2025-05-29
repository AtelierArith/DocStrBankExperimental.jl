```
pitchshift(audio::SampleBuf{T, N}, semitones::Real = 8)
```

Returns pitchshifted audio waveform

# Output

Return the pitchshifted audio waveform as a SampleBuf{T, N}.

# Arguments

## `audio`

An audio of type SampleBuf{T, N} whose pitch is to be shifted.

## `semitones`

A parameter used to define the new sample rate for the audio.

`new samplerate` = 2.0 ^ (semitones / 12.0)

# Example

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(10000), 10)
audio_two_channel = SampleBuf(rand(10000, 2), 10)
audio_multi_channel = SampleBuf(rand(10000, 4), 10)

pitchshift(audio_one_channel, 8)
pitchshift(audio_two_channel, 8)
pitchshift(audio_multi_channel, 8)

```
