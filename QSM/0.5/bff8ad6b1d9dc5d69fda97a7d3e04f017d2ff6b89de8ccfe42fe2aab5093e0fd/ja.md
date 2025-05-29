```
lap(
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> typeof(similar(u))
```

二次中心差分ラプラシアン。

### 引数

  * `u::AbstractArray{<:AbstractFloat, 3}`: 入力配列
  * `h::NTuple{3, Real}`: グリッド間隔

### 戻り値

  * `d2u::typeof(similar(u))`: `u` の離散ラプラシアン
