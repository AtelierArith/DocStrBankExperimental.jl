```
compile(stream::PortAudioStream, audio_schedule::AudioSchedule)
```

Compile an AudioSchedule by only writing the first sample from each segment to the stream buffer.

```jldoctest
julia> using AudioSchedules

julia> audio_schedule = AudioSchedule();

julia> push!(audio_schedule, Map(sin, Cycles(440Hz)), 0s, @envelope(
            0,
            Line => 1s,
            1,
            Line => 1s,
            0,
        ));

julia> using PortAudio: PortAudioStream

julia> PortAudioStream(0, 1) do stream
            compile(stream, audio_schedule)
        end
```
