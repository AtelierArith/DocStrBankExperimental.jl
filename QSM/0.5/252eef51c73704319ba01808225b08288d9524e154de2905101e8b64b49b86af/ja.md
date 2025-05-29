```
gradfp!(
    dx::AbstractArray{<:AbstractFloat, 3},
    dy::AbstractArray{<:AbstractFloat, 3},
    dz::AbstractArray{<:AbstractFloat, 3},
    u::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real},
) -> (dx, dy, dz)
```

周期境界を持つ一次前方差分勾配。

### 引数

  * `dx::AbstractArray{<:AbstractFloat, 3}`: `u` の勾配の x 成分
  * `dy::AbstractArray{<:AbstractFloat, 3}`: `u` の勾配の y 成分
  * `dz::AbstractArray{<:AbstractFloat, 3}`: `u` の勾配の z 成分
  * `u::AbstractArray{<:AbstractFloat, 3}`: 入力配列
  * `h::NTuple{3, Real}`: グリッド間隔

### 戻り値

  * `dx`: `u` の勾配の x 成分
  * `dy`: `u` の勾配の y 成分
  * `dz`: `u` の勾配の z 成分
