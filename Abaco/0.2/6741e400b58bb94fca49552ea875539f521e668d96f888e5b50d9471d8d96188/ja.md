```
last_point(abaco, ne::String, var::String)::Union{Nothing, Missing, Tuple{Int,Float64}}
```

`ne`ノードメトリック`var`の最新の時間値をタプル(time, value)として返します。

ノード`ne`が不明な場合は`nothing`を返し、メトリック`var`の値がない場合は`missing`を返します。
