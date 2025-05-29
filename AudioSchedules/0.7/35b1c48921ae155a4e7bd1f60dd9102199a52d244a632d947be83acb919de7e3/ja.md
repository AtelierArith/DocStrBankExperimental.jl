```
Map(a_function, synthesizers...)
```

`synthesizers`に対して`a_function`を適用します。[`make_series`](@ref)をサポートしています。

```jldoctest
julia> using AudioSchedules


julia> first(make_series(Map(sin, Cycles(440Hz)), 44100Hz))
0.06264832417874369
```
