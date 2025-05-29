```
nekf_train(ins::INS, meas, itp_mapS, x_nn::Matrix, y_nn::Matrix;
           P0                   = create_P0(),
           Qd                   = create_Qd(),
           R                    = 1.0,
           baro_tau             = 3600.0,
           acc_tau              = 3600.0,
           gyro_tau             = 3600.0,
           fogm_tau             = 600.0,
           η_adam               = 0.1,
           epoch_adam::Int      = 10,
           hidden::Int          = 1,
           activation::Function = swish,
           l_window::Int        = 50,
           date                 = get_years(2020,185),
           core::Bool           = false)
```

航空磁気異常ナビゲーションのための測定ノイズ共分散適応型ニューラル拡張カルマンフィルタ（nEKF）モデルをトレーニングします。

**引数:**

  * `ins`:        `INS` 慣性航法システム構造体
  * `meas`:       スカラー磁力計測定 [nT]
  * `itp_mapS`:   スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `x_nn`:       ニューラルネットワーク用の `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `y_nn`:       ニューラルネットワーク用の `y` ターゲット行列（`[latitude longitude]`）
  * `P0`:         （オプション）初期共分散行列
  * `Qd`:         （オプション）離散時間プロセス/システムノイズ行列
  * `R`:          （オプション）測定（ホワイト）ノイズ分散
  * `baro_tau`:   （オプション）気圧計の時間定数 [s]
  * `acc_tau`:    （オプション）加速度計の時間定数 [s]
  * `gyro_tau`:   （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`:   （オプション）FOGMのキャッチオール時間定数 [s]
  * `η_adam`:     （オプション）Adamオプティマイザの学習率
  * `epoch_adam`: （オプション）Adamオプティマイザのエポック数
  * `hidden`:     （オプション）隠れ層とノード（例：`[8,8]` は2つの隠れ層、各8ノード）
  * `activation`: （オプション）活性化関数

      * `relu`  = 修正線形ユニット
      * `σ`     = シグモイド（ロジスティック関数）
      * `swish` = セルフゲーテッド
      * `tanh`  = 双曲線タンジェント
      * 視覚的には `plot_activation()` を実行
  * `l_window`:   （オプション）時間ウィンドウの長さ
  * `date`:       （オプション）IGRF用の測定日（小数年）[年]
  * `core`:       （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `m`: ニューラルネットワークモデル
