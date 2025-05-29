```
ODProblem{D, T <: Real, WT <: AbstractWeightingScheme{T},
    DT <: AbstractDebiasingScheme{T}}
```

軌道決定問題。

## フィールド

  * `dynamics::D`: 動力学モデル。
  * `radec::Vector{RadecMPC{T}}`: 光学天体測定のベクトル。
  * `tracklets::Vector{Tracklet{T}}`: トラックレットのベクトル。
  * `w8s::WT`: 重み付けスキーム。
  * `bias::DT`: デバイアススキーム。
