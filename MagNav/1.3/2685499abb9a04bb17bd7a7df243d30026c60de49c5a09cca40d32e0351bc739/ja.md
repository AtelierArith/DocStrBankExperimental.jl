```
ekf_online(lat, lon, alt, vn, ve, vd, fn, fe, fd, Cnb, meas,
           Bx, By, Bz, dt, itp_mapS, x0_TL, P0, Qd, R;
           baro_tau   = 3600.0,
           acc_tau    = 3600.0,
           gyro_tau   = 3600.0,
           fogm_tau   = 600.0,
           date       = get_years(2020,185),
           core::Bool = false,
           terms      = [:permanent,:induced,:eddy,:bias],
           Bt_scale   = 50000)
```

オンライン学習を伴う拡張カルマンフィルタ（EKF）によるトレス-ローソン係数の推定。

**引数:**

  * `lat`:          緯度  [rad]
  * `lon`:          経度 [rad]
  * `alt`:          高度  [m]
  * `vn`:           北方向の速度 [m/s]
  * `ve`:           東方向の速度 [m/s]
  * `vd`:           下方向の速度 [m/s]
  * `fn`:           北方向の特定の力 [m/s^2]
  * `fe`:           東方向の特定の力 [m/s^2]
  * `fd`:           下方向の特定の力 [m/s^2]
  * `Cnb`:          方向余弦行列（ボディからナビゲーション） [-]
  * `meas`:         スカラー磁力計測定 [nT]
  * `Bx`,`By`,`Bz`: ベクトル磁力計測定 [nT]
  * `dt`:           測定時間ステップ [s]
  * `itp_mapS`:     スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `x0_TL`:        初期トレス-ローソン係数状態
  * `P0`:           初期共分散行列
  * `Qd`:           離散時間プロセス/システムノイズ行列
  * `R`:            測定（ホワイト）ノイズ分散
  * `baro_tau`:     （オプション）気圧計の時間定数 [s]
  * `acc_tau`:      （オプション）加速度計の時間定数 [s]
  * `gyro_tau`:     （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`:     （オプション）FOGMの全体的な時間定数 [s]
  * `date`:         （オプション）IGRF用の測定日（小数年） [yr]
  * `core`:         （オプション）trueの場合、測定にコア磁場を含める
  * `terms`:        （オプション）使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `Bt_scale`:     （オプション）誘導および渦電流項のスケーリングファクター [nT]

**戻り値:**

  * `filt_res`: `FILTres` フィルタ結果構造体
