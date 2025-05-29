```
(ekf_rt::EKF_RT)(ins::INS, meas, itp_mapS;
                 der_mapS = nothing,
                 map_alt  = -1)
```

空中磁気異常ナビゲーションのためのリアルタイム (RT) 拡張カルマンフィルタ (EKF)。個々のサンプルを受信し、`ekf_rt` 構造体内で時間、共分散行列、状態ベクトル、および測定残差を更新します。

**引数:**

  * `ekf_rt`:   `EKF_RT` リアルタイム拡張カルマンフィルタ構造体
  * `ins`:      個々のサンプルを持つ慣性ナビゲーションシステム構造体 (`ins.N=1`)
  * `meas`:     スカラー磁力計測定 [nT]
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `der_mapS`: (オプション) スカラー地図の垂直導関数補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `map_alt`:  (オプション) 地図の高度 [m]

**戻り値:**

  * `filt_res`: `FILTres` フィルタ結果構造体、
  * `ekf_rt`:   `t`, `P`, `x`, および `r` フィールドが変更されます
