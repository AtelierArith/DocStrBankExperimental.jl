```
duration(audio::SampleBuf)
```

Returns the duration of given audio, in seconds

# Output

Return the duration of audio(in seconds).

# Arguments

## `audio`

An audio of type SampleBuf whose duration is to be found.

# Example

```julia
using MusicProcessing

audio_one_channel = SampleBuf(rand(1000), 10)
audio_two_channel = SampleBuf(rand(1000, 2), 10)
audio_multi_channel = SampleBuf(rand(1000, 4), 10)

duration(audio_one_channel)
duration(audio_two_channel)
duration(audio_multi_channel)
```
