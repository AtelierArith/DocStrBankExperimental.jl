```
Grow(start_level, duration, end_level)
```

Exponentially grow or decay from `start_level` to `end_level` over a `duration` in time units like `s`. Supports [`make_series`](@ref).

```jldoctest
julia> using AudioSchedules


julia> using Unitful: Hz, s


julia> first(make_series(Grow(0.1, 1s, 1), 44100Hz))
0.10000522141770128
```
