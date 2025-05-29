```
ekf_online(ins::INS, meas, flux::MagV, itp_mapS, x0_TL, P0, Qd, R;
           baro_tau   = 3600.0,
           acc_tau    = 3600.0,
           gyro_tau   = 3600.0,
           fogm_tau   = 600.0,
           date       = get_years(2020,185),
           core::Bool = false,
           terms      = [:permanent,:induced,:eddy,:bias],
           Bt_scale   = 50000)
```

トレルス-ローソン係数のオンライン学習を伴う拡張カルマンフィルタ（EKF）。

**引数:**

  * `ins`:      `INS`慣性航法システム構造体
  * `meas`:     スカラー磁力計測定 [nT]
  * `flux`:     `MagV`ベクトル磁力計測定構造体
  * `itp_mapS`: スカラー地図補間関数（`f(lat,lon)`または`f(lat,lon,alt)`）
  * `x0_TL`:    初期トレルス-ローソン係数状態
  * `P0`:       初期共分散行列
  * `Qd`:       離散時間プロセス/システムノイズ行列
  * `R`:        測定（ホワイト）ノイズ分散
  * `baro_tau`: （オプション）気圧計時間定数 [s]
  * `acc_tau`:  （オプション）加速度計時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープ時間定数 [s]
  * `fogm_tau`: （オプション）FOGMキャッチオール時間定数 [s]
  * `date`:     （オプション）IGRF用の測定日（小数年） [年]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める
  * `terms`:    （オプション）使用するトレルス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `Bt_scale`: （オプション）誘導および渦電流項のスケーリング係数 [nT]

**戻り値:**

  * `filt_res`: `FILTres`フィルタ結果構造体
