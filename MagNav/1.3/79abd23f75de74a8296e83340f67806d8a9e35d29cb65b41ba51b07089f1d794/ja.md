```
FILTout{T1 <: Signed, T2 <: AbstractFloat} <: Path{T1, T2}
```

フィルタ抽出出力構造体。`Path`のサブタイプ。

| **フィールド**  | **型**        | **説明**                    |
|:---------- |:------------ |:------------------------- |
| `N`        | `T1`         | サンプル数（インスタンス数）            |
| `dt`       | `T2`         | 測定時間ステップ [s]              |
| `tt`       | Vector{`T2`} | 時間 [s]                    |
| `lat`      | Vector{`T2`} | 緯度 [rad]                  |
| `lon`      | Vector{`T2`} | 経度 [rad]                  |
| `alt`      | Vector{`T2`} | 高度 [m]                    |
| `vn`       | Vector{`T2`} | 北方向の速度 [m/s]              |
| `ve`       | Vector{`T2`} | 東方向の速度 [m/s]              |
| `vd`       | Vector{`T2`} | 下方向の速度 [m/s]              |
| `tn`       | Vector{`T2`} | 北方向の傾き（姿勢） [rad]          |
| `te`       | Vector{`T2`} | 東方向の傾き（姿勢） [rad]          |
| `td`       | Vector{`T2`} | 下方向の傾き（姿勢） [rad]          |
| `ha`       | Vector{`T2`} | バロメーター補助高度 [m]            |
| `ah`       | Vector{`T2`} | バロメーター補助垂直加速度 [m/s^2]     |
| `ax`       | Vector{`T2`} | x加速度計 [m/s^2]             |
| `ay`       | Vector{`T2`} | y加速度計 [m/s^2]             |
| `az`       | Vector{`T2`} | z加速度計 [m/s^2]             |
| `gx`       | Vector{`T2`} | xジャイロスコープ [rad/s]         |
| `gy`       | Vector{`T2`} | yジャイロスコープ [rad/s]         |
| `gz`       | Vector{`T2`} | zジャイロスコープ [rad/s]         |
| `fogm`     | Vector{`T2`} | FOGMキャッチオール [nT]          |
| `lat_std`  | Vector{`T2`} | 緯度 1-σ [rad]              |
| `lon_std`  | Vector{`T2`} | 経度 1-σ [rad]              |
| `alt_std`  | Vector{`T2`} | 高度 1-σ [m]                |
| `vn_std`   | Vector{`T2`} | 北方向の速度 1-σ [m/s]          |
| `ve_std`   | Vector{`T2`} | 東方向の速度 1-σ [m/s]          |
| `vd_std`   | Vector{`T2`} | 下方向の速度 1-σ [m/s]          |
| `tn_std`   | Vector{`T2`} | 北方向の傾き（姿勢） 1-σ [rad]      |
| `te_std`   | Vector{`T2`} | 東方向の傾き（姿勢） 1-σ [rad]      |
| `td_std`   | Vector{`T2`} | 下方向の傾き（姿勢） 1-σ [rad]      |
| `ha_std`   | Vector{`T2`} | バロメーター補助高度 1-σ [m]        |
| `ah_std`   | Vector{`T2`} | バロメーター補助垂直加速度 1-σ [m/s^2] |
| `ax_std`   | Vector{`T2`} | x加速度計 1-σ [m/s^2]         |
| `ay_std`   | Vector{`T2`} | y加速度計 1-σ [m/s^2]         |
| `az_std`   | Vector{`T2`} | z加速度計 1-σ [m/s^2]         |
| `gx_std`   | Vector{`T2`} | xジャイロスコープ 1-σ [rad/s]     |
| `gy_std`   | Vector{`T2`} | yジャイロスコープ 1-σ [rad/s]     |
| `gz_std`   | Vector{`T2`} | zジャイロスコープ 1-σ [rad/s]     |
| `fogm_std` | Vector{`T2`} | FOGMキャッチオール 1-σ [nT]      |
| `n_std`    | Vector{`T2`} | 北方向 1-σ [m]               |
| `e_std`    | Vector{`T2`} | 東方向 1-σ [m]               |
| `lat_err`  | Vector{`T2`} | 緯度 エラー [rad]              |
| `lon_err`  | Vector{`T2`} | 経度 エラー [rad]              |
| `alt_err`  | Vector{`T2`} | 高度 エラー [m]                |
| `vn_err`   | Vector{`T2`} | 北方向の速度 エラー [m/s]          |
| `ve_err`   | Vector{`T2`} | 東方向の速度 エラー [m/s]          |
| `vd_err`   | Vector{`T2`} | 下方向の速度 エラー [m/s]          |
| `tn_err`   | Vector{`T2`} | 北方向の傾き（姿勢） エラー [rad]      |
| `te_err`   | Vector{`T2`} | 東方向の傾き（姿勢） エラー [rad]      |
| `td_err`   | Vector{`T2`} | 下方向の傾き（姿勢） エラー [rad]      |
| `n_err`    | Vector{`T2`} | 北方向 エラー [m]               |
| `e_err`    | Vector{`T2`} | 東方向 エラー [m]               |

```
