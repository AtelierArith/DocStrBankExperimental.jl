```
Line(start_level, duration, end_level)
```

`start_level`から`end_level`までの線で、`s`のような時間単位での`duration`を持ちます。 [`make_series`](@ref)をサポートしています。

```jldoctest
julia> using AudioSchedules


julia> first(make_series(Line(0, 1s, 1), 44100Hz))
2.2675736961451248e-5
```
