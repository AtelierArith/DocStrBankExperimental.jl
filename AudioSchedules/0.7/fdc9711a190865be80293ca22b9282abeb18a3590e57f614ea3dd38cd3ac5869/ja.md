```
Cycles(frequency)
```

周波数（`Hz`などの周波数単位）で繰り返すために0から2πまでのサイクル。 [`make_series`](@ref)をサポートしています。

```jldoctest
julia> using AudioSchedules


julia> using Unitful: Hz


julia> first(make_series(Cycles(440Hz), 44100Hz))
0.06268937721449021
```
