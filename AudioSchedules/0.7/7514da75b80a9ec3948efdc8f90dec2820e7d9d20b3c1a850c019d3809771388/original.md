```
push!(audio_schedule::AudioSchedule, synthesizer, start_time,
    start_level, shape => duration, end_level, more_segments...
)
```

Add a synthesizer to a [`AudioSchedule`](@ref), where `synthesizer` is anything that supports [`make_series`](@ref), `start_time` has units of time (like `s`), and the rest of the arguments specify the shape of the envelope.

For all envelope [`segment`](@ref), call

```
segment(shape, start_level, duration, end_level)
```

`duration` should have units of time (like `s`). For example,

```
push!(audio_schedule, synthesizer, start_time, @envelope(0, Line => 1s, 1, Line => 1s, 0))
```

will call segment twice:

```
segment(Line, 0, 1s, 1)
segment(Line, 1, 1s, 0)
```
