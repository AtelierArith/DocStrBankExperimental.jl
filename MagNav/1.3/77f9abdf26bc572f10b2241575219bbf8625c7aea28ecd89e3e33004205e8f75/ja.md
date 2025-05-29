```
INSout{T2 <: AbstractFloat}
```

慣性航法システムから抽出された出力構造体。

| **フィールド** | **型**        | **説明**         |
|:--------- |:------------ |:-------------- |
| `lat_std` | Vector{`T2`} | 緯度 1-σ [ラジアン]  |
| `lon_std` | Vector{`T2`} | 経度 1-σ [ラジアン]  |
| `alt_std` | Vector{`T2`} | 高度 1-σ [メートル]  |
| `n_std`   | Vector{`T2`} | 北方向 1-σ [メートル] |
| `e_std`   | Vector{`T2`} | 東方向 1-σ [メートル] |
| `lat_err` | Vector{`T2`} | 緯度 誤差 [ラジアン]   |
| `lon_err` | Vector{`T2`} | 経度 誤差 [ラジアン]   |
| `alt_err` | Vector{`T2`} | 高度 誤差 [メートル]   |
| `n_err`   | Vector{`T2`} | 北方向 誤差 [メートル]  |
| `e_err`   | Vector{`T2`} | 東方向 誤差 [メートル]  |
