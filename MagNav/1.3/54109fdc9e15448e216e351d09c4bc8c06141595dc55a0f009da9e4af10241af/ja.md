```
CRLBout{T2 <: AbstractFloat}
```

Cramér–Rao下限抽出出力構造体。

| **フィールド**  | **型**        | **説明**             |
|:---------- |:------------ |:------------------ |
| `lat_std`  | Vector{`T2`} | 緯度 1-σ [rad]       |
| `lon_std`  | Vector{`T2`} | 経度 1-σ [rad]       |
| `alt_std`  | Vector{`T2`} | 高度 1-σ [m]         |
| `vn_std`   | Vector{`T2`} | 北向き速度 1-σ [m/s]    |
| `ve_std`   | Vector{`T2`} | 東向き速度 1-σ [m/s]    |
| `vd_std`   | Vector{`T2`} | 下向き速度 1-σ [m/s]    |
| `tn_std`   | Vector{`T2`} | 北向き傾き（姿勢）1-σ [rad] |
| `te_std`   | Vector{`T2`} | 東向き傾き（姿勢）1-σ [rad] |
| `td_std`   | Vector{`T2`} | 下向き傾き（姿勢）1-σ [rad] |
| `fogm_std` | Vector{`T2`} | FOGM 1-σ [nT]      |
| `n_std`    | Vector{`T2`} | 北方向 1-σ [m]        |
| `e_std`    | Vector{`T2`} | 東方向 1-σ [m]        |
