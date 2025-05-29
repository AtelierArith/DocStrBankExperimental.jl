```
Grow(start_level, duration, end_level)
```

`start_level`から`end_level`までを`duration`の時間単位（例えば`s`）で指数的に成長または減衰させます。 [`make_series`](@ref)をサポートしています。

```jldoctest
julia> using AudioSchedules


julia> using Unitful: Hz, s


julia> first(make_series(Grow(0.1, 1s, 1), 44100Hz))
0.10000522141770128
```
