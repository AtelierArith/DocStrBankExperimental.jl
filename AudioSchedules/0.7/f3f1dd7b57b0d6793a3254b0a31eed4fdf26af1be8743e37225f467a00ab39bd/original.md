```
Line(start_level, duration, end_level)
```

A line from `start_level` to `end_level` with a `duration` in time units like `s`. Supports [`make_series`](@ref).

```jldoctest
julia> using AudioSchedules


julia> first(make_series(Line(0, 1s, 1), 44100Hz))
2.2675736961451248e-5
```
