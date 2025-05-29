```
nekf(lat, lon, alt, vn, ve, vd, fn, fe, fd, Cnb, meas, dt, itp_mapS,
     x_nn::Matrix = meas[:,:],
     m            = Dense(1 => 1);
     P0           = create_P0(),
     Qd           = create_Qd(),
     R            = 1.0,
     baro_tau     = 3600.0,
     acc_tau      = 3600.0,
     gyro_tau     = 3600.0,
     fogm_tau     = 600.0,
     date         = get_years(2020,185),
     core::Bool   = false)
```

航空磁気異常ナビゲーションのための測定ノイズ共分散適応型ニューラル拡張カルマンフィルタ（nEKF）。

**引数:**

  * `lat`:      緯度  [rad]
  * `lon`:      経度 [rad]
  * `alt`:      高度  [m]
  * `vn`:       北方向の速度 [m/s]
  * `ve`:       東方向の速度 [m/s]
  * `vd`:       下方向の速度 [m/s]
  * `fn`:       北方向の特定の力 [m/s^2]
  * `fe`:       東方向の特定の力 [m/s^2]
  * `fd`:       下方向の特定の力 [m/s^2]
  * `Cnb`:      方向余弦行列（体からナビゲーション） [-]
  * `meas`:     スカラー磁力計測定 [nT]
  * `dt`:       測定時間ステップ [s]
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `x_nn`:     `N` x `Nf` データ行列（ニューラルネットワーク用） (`Nf` は特徴の数)
  * `m`:        ニューラルネットワークモデル
  * `P0`:       （オプション）初期共分散行列
  * `Qd`:       （オプション）離散時間プロセス/システムノイズ行列
  * `R`:        （オプション）測定（ホワイト）ノイズ分散
  * `baro_tau`: （オプション）気圧計の時間定数 [s]
  * `acc_tau`:  （オプション）加速度計の時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`: （オプション）FOGMの全般的な時間定数 [s]
  * `date`:     （オプション）IGRF用の測定日（小数年） [yr]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `filt_res`: `FILTres` フィルタ結果構造体
