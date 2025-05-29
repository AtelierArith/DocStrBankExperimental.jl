```
lap!(
    d2u::AbstractArray{<:AbstractFloat, 3},
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> d2u
```

二次中心差分ラプラシアン。

### 引数

  * `d2u::AbstractArray{<:AbstractFloat, 3}`: `u` の離散ラプラシアン
  * `u::AbstractArray{<:AbstractFloat, 3}`: 入力配列
  * `h::NTuple{3, Real}`: グリッド間隔

### 戻り値

  * `d2u`: `u` の離散ラプラシアン
