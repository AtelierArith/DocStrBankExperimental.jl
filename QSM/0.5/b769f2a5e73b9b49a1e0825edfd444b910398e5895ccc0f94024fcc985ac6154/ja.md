```
gradfp(
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> NTuple{3, typeof(similar(u))}
```

周期境界を持つ一次前方差分勾配。

### 引数

  * `u::AbstractArray{<:AbstractFloat, 3}`: 入力配列
  * `h::NTuple{3, Real}`: グリッド間隔

### 戻り値

  * `dx::typeof(similar(u))`: `u`の勾配のx成分
  * `dy::typeof(similar(u))`: `u`の勾配のy成分
  * `dz::typeof(similar(u))`: `u`の勾配のz成分
