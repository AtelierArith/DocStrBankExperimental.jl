```
Map(a_function, synthesizers...)
```

Map `a_function` over `synthesizers`. Supports [`make_series`](@ref).

```jldoctest
julia> using AudioSchedules


julia> first(make_series(Map(sin, Cycles(440Hz)), 44100Hz))
0.06264832417874369
```
