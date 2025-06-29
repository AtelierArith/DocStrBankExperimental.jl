```
mpf(lat, lon, alt, vn, ve, vd, fn, fe, fd, Cnb, meas, dt, itp_mapS;
    P0         = create_P0(),
    Qd         = create_Qd(),
    R          = 1.0,
    num_part   = 1000,
    thresh     = 0.8,
    baro_tau   = 3600.0,
    acc_tau    = 3600.0,
    gyro_tau   = 3600.0,
    fogm_tau   = 600.0,
    date       = get_years(2020,185),
    core::Bool = false)
```

空中磁気異常ナビゲーションのためのRao-Blackwellized（周辺化された）粒子フィルタ（MPF）。この簡略化されたMPFは、LINEARダイナミクスでのみ機能します。これにより、各粒子に同じカルマンフィルタの共分散行列を使用でき、フィルタが簡素化され、計算負荷が軽減されます。これは、非常に非線形で非ガウス的な測定がある地図マッチングナビゲーションに特に適していますが、非線形ダイナミクスではありません。また、フィルタは計算を高速化するために非相関測定を仮定します。

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
  * `Cnb`:      方向余弦行列（ボディからナビゲーション） [-]
  * `meas`:     スカラー磁力計測定 [nT]
  * `dt`:       測定時間ステップ [s]
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `P0`:       （オプション）初期共分散行列
  * `Qd`:       （オプション）離散時間プロセス/システムノイズ行列
  * `R`:        （オプション）測定（ホワイト）ノイズ分散
  * `num_part`: （オプション）粒子の数
  * `thresh`:   （オプション）再サンプリング閾値比 {0:1}
  * `baro_tau`: （オプション）気圧計の時間定数 [s]
  * `acc_tau`:  （オプション）加速度計の時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`: （オプション）FOGMのキャッチオール時間定数 [s]
  * `date`:     （オプション）IGRFのための測定日（小数年） [yr]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `filt_res`: `FILTres` フィルタ結果構造体
