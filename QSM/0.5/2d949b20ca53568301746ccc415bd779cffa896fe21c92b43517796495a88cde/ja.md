```
crop_indices(x::AbstractArray, out = 0) -> CartesianIndices
```

マスクを切り取るためのインデックス。

### 引数

  * `x::AbstractArray`: マスク
  * `out = 0`: `x`内で外部と見なされる値

### 戻り値

  * `CartesianIndices`: マスクを切り取るためのインデックス
