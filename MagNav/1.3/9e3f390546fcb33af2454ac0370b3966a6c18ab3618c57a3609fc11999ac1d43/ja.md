```
(ekf_rt::EKF_RT)(lat, lon, alt, vn, ve, vd, fn, fe, fd,
                 Cnb, meas, t, itp_mapS;
                 der_mapS = nothing,
                 map_alt  = -1,
                 dt       = 0.1)
```

航空磁気異常ナビゲーションのためのリアルタイム (RT) 拡張カルマンフィルタ (EKF)。個々のサンプルを受信し、`ekf_rt` 構造体内の時間、共分散行列、状態ベクトル、および測定残差を更新します。

**引数:**

  * `ekf_rt`:   `EKF_RT` リアルタイム拡張カルマンフィルタ構造体
  * `lat`:      緯度  [rad]
  * `lon`:      経度 [rad]
  * `alt`:      高度  [m]
  * `vn`:       北方向の速度 [m/s]
  * `ve`:       東方向の速度 [m/s]
  * `vd`:       下方向の速度 [m/s]
  * `fn`:       北方向の特定の力 [m/s^2]
  * `fe`:       東方向の特定の力 [m/s^2]
  * `fd`:       下方向の特定の力 [m/s^2]
  * `Cnb`:      方向余弦行列 (体からナビゲーション) [-]
  * `meas`:     スカラー磁力計測定 [nT]
  * `t`:        時間 [s]
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `der_mapS`: (オプション) スカラー地図の垂直導関数補間関数 (`f(lat,lon)` または (`f(lat,lon,alt)`)
  * `map_alt`:  (オプション) 地図の高度 [m]
  * `dt`:       (オプション) 測定時間ステップ [s]、`ekf_rt.t < 0` の場合のみ使用

**戻り値:**

  * `filt_res`: `FILTres` フィルタ結果構造体、
  * `ekf_rt`:   `t`, `P`, `x`, & `r` フィールドが変更されます
