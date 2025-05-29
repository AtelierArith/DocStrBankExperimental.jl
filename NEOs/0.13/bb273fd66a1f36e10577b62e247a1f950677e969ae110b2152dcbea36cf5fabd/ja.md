```
ODProblem(dynamics::D, radec::Vector{RadecMPC{T}} [,
    w8s::WT [, bias::DT]]) where {D, T <: Real, WT, DT}
```

軌道決定問題を返します。

## 引数

  * `dynamics::D`: 動力学モデル。
  * `radec::Vector{RadecMPC{T}}`: 光学天体測定のベクトル。
  * `w8s::WT`: 重み付けスキーム（デフォルト: `Veres17`）。
  * `bias::DT`: デバイアススキーム（デフォルト: `Eggl20`）。
