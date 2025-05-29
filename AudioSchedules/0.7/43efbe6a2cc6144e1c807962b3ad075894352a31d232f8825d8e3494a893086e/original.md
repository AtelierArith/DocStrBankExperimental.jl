```
duration(audio_schedule::AudioSchedule)
```

Find the duration of an `AudioSchedule` in seconds.

```jldoctest
julia> using AudioSchedules

julia> audio_schedule = AudioSchedule();

julia> push!(audio_schedule, Map(sin, Cycles(440Hz)), 0s, @envelope(
            0,
            Line => 1s,
            1,
            Line => 1s,
            0,
        ))

julia> duration(audio_schedule)
2.0 s
```
