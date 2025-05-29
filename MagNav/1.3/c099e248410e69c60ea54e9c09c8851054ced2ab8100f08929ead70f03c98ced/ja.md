```
MapV{T2 <: AbstractFloat} <: Map{T2}
```

ベクトル磁気異常マップ構造体。`Map`のサブタイプ。

| **フィールド** | **型**        | **説明**                        |
|:--------- |:------------ |:----------------------------- |
| `info`    | String       | マップ情報                         |
| `mapX`    | Matrix{`T2`} | `ny` x `nx` x方向の磁気異常マップ [nT]  |
| `mapY`    | Matrix{`T2`} | `ny` x `nx` y方向の磁気異常マップ [nT]  |
| `mapZ`    | Matrix{`T2`} | `ny` x `nx` z方向の磁気異常マップ [nT]  |
| `xx`      | Vector{`T2`} | `nx` マップx方向（経度）座標 [rad]       |
| `yy`      | Vector{`T2`} | `ny` マップy方向（緯度）座標 [rad]       |
| `alt`     | `T2`         | マップ高度 [m]                     |
| `mask`    | BitMatrix    | `ny` x `nx` 有効（未記入）マップデータのマスク |
