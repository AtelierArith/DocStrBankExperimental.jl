```
ekf_online_nn(ins::INS, meas, itp_mapS, x_nn, m, y_norms, P0, Qd, R;
              baro_tau   = 3600.0,
              acc_tau    = 3600.0,
              gyro_tau   = 3600.0,
              fogm_tau   = 600.0,
              date       = get_years(2020,185),
              core::Bool = false)
```

オンライン学習によるニューラルネットワーク重みの拡張カルマンフィルタ（EKF）。

**引数:**

  * `ins`:      `INS`慣性航法システム構造体
  * `meas`:     スカラー磁力計測定 [nT]
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `x_nn`:     ニューラルネットワーク用の `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `m`:        スキップ接続では動作しないニューラルネットワークモデル
  * `y_norms`:  長さ `2` のタプル `y` 正規化、`(y_bias,y_scale)`
  * `P0`:       初期共分散行列
  * `Qd`:       離散時間プロセス/システムノイズ行列
  * `R`:        測定（ホワイト）ノイズ分散
  * `baro_tau`: （オプション）気圧計時間定数 [s]
  * `acc_tau`:  （オプション）加速度計時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープ時間定数 [s]
  * `fogm_tau`: （オプション）FOGMのキャッチオール時間定数 [s]
  * `date`:     （オプション）IGRF用の測定日（小数年） [年]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `filt_res`: `FILTres` フィルタ結果構造体
