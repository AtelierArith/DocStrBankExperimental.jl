```
timerange = TimeRange(t_start, t_end)
```

`TimeRange`関数は`TimeCurve`構造体のカスタムコンストラクタです。開始時刻と終了時刻を持つ単純な時間間隔を定義することができます。

# 引数

  * `t_start`: (`::Real`, `[s]`, `=0.0`) 開始時刻
  * `t_end`: (`::Real`, `[s]`, `=1.0`) 終了時刻

# 戻り値

  * `timerange`: (`::TimeCurve`) TimeCurve構造体

# 例

```julia-repl
julia> timerange = TimeRange(t_start=0.6, t_end=1.4)
```

![Time Range](../assets/time-range.svg)
