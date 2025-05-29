```
ekf(ins::INS, meas, itp_mapS;
    P0         = create_P0(),
    Qd         = create_Qd(),
    R          = 1.0,
    baro_tau   = 3600.0,
    acc_tau    = 3600.0,
    gyro_tau   = 3600.0,
    fogm_tau   = 600.0,
    date       = get_years(2020,185),
    core::Bool = false,
    der_mapS   = map_itp(zeros(2,2),[-pi,pi],[-pi/2,pi/2]),
    map_alt    = 0)
```

空中磁気異常ナビゲーションのための拡張カルマンフィルタ（EKF）。

**引数:**

  * `ins`:      `INS`慣性ナビゲーションシステム構造体
  * `meas`:     スカラー磁力計測定 [nT]
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `P0`:       （オプション）初期共分散行列
  * `Qd`:       （オプション）離散時間プロセス/システムノイズ行列
  * `R`:        （オプション）測定（ホワイト）ノイズ分散
  * `baro_tau`: （オプション）気圧計の時間定数 [s]
  * `acc_tau`:  （オプション）加速度計の時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`: （オプション）FOGMのキャッチオール時間定数 [s]
  * `date`:     （オプション）IGRFのための測定日（小数年） [年]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める
  * `der_mapS`: （オプション）スカラー地図の垂直導関数地図補間関数 (`f(lat,lon)` または (`f(lat,lon,alt)`)
  * `map_alt`:  （オプション）地図の高度 [m]

**戻り値:**

  * `filt_res`: `FILTres`フィルタ結果構造体
