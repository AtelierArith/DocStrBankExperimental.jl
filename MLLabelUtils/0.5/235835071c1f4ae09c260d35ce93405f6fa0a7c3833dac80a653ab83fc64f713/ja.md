```
labelfreq(obj) -> Dict
```

`obj`内の各ラベルの絶対頻度を計算します。

```
julia> labelfreq([0, 1, 1, 0, 0])
Dict{Int64,Int64} with 2 entries:
  0 => 3
  1 => 2
```
