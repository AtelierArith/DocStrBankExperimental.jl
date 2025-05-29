```
gradfp_adj!(
    u::AbstractArray{<:AbstractFloat, 3}
    dx::AbstractArray{<:AbstractFloat, 3},
    dy::AbstractArray{<:AbstractFloat, 3},
    dz::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> u
```

周期境界を持つ一次前方差分勾配の随伴。

### 引数

  * `u::AbstractArray{<:AbstractFloat, 3}`: [dx, dy, dz] の発散
  * `dx::AbstractArray{<:AbstractFloat, 3}`: x成分
  * `dy::AbstractArray{<:AbstractFloat, 3}`: y成分
  * `dz::AbstractArray{<:AbstractFloat, 3}`: z成分
  * `h::NTuple{3, Real}`: グリッド間隔

### 戻り値

  * `u`: [dx, dy, dz] の発散
