```
raan_to_ltdn(raan::Number, t::Union{Number, DateTime}) -> Float64
```

与えられた瞬間 `t` [UT1] における昇交点の地方時 (LTDN) を計算します。

`t` はユリウス日 [UT1] または `DateTime` [UT1] として表すことができます。
