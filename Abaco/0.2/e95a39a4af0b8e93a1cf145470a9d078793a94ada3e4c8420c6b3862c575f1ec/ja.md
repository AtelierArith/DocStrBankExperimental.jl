```
last_value(abaco, ne::String, var::String)::Union{Nothing, Missing, Float64}
```

`ne`ノードメトリック`var`の最新の時間値を返します。

ノード`ne`が不明な場合は`nothing`を返し、メトリック`var`の値がない場合は`missing`を返します。
