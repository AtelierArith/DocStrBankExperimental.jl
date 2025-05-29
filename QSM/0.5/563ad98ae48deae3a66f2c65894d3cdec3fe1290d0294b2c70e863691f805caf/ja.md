```
gradfp_adj(
    dx::AbstractArray{<:AbstractFloat, 3},
    dy::AbstractArray{<:AbstractFloat, 3},
    dz::AbstractArray{<:AbstractFloat, 3},
    h::NTuple{3, Real}
) -> typeof(similar(dx, promote_eltype(dx, dy, dz)))
```

周期境界を持つ一次前方差分勾配の随伴。

### 引数

  * `dx::AbstractArray{<:AbstractFloat, 3}`: x成分
  * `dy::AbstractArray{<:AbstractFloat, 3}`: y成分
  * `dz::AbstractArray{<:AbstractFloat, 3}`: z成分
  * `h::NTuple{3, Real}`: グリッド間隔

### 戻り値

  * `u::typeof(similar(dx, promote_eltype(dx, dy ,dz)))`: [dx, dy, dz] の発散
