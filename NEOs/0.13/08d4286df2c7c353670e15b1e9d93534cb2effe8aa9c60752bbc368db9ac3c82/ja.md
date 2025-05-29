```
curvature(radec::AbstractVector{RadecMPC{T}}) where {T <: Real}
```

返す:

  * `radec`の測地線曲率と沿道加速度を持つベクトル。
  * 曲率共分散行列。

!!! reference
    https://doi.org/10.1016/j.icarus.2007.11.033の5.1節を参照してください。

