```
nekf(ins::INS, meas, itp_mapS,
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

  * `ins`:      `INS`慣性ナビゲーションシステム構造体
  * `meas`:     スカラー磁力計測定 [nT]
  * `itp_mapS`: スカラー地図補間関数（`f(lat,lon)`または`f(lat,lon,alt)`）
  * `x_nn`:     ニューラルネットワーク用の`N` x `Nf`データ行列（`Nf`は特徴の数）
  * `m`:        ニューラルネットワークモデル
  * `P0`:       （オプション）初期共分散行列
  * `Qd`:       （オプション）離散時間プロセス/システムノイズ行列
  * `R`:        （オプション）測定（ホワイト）ノイズ分散
  * `baro_tau`: （オプション）気圧計の時間定数 [s]
  * `acc_tau`:  （オプション）加速度計の時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`: （オプション）FOGMの全般的な時間定数 [s]
  * `date`:     （オプション）IGRFのための測定日（小数年） [年]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `filt_res`: `FILTres`フィルタ結果構造体
