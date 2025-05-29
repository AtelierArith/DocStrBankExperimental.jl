```
nekf_train(xyz::XYZ, ind, meas, itp_mapS, x::Matrix;
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

空中磁気異常ナビゲーションのための測定ノイズ共分散適応型ニューラル拡張カルマンフィルタ（nEKF）モデルをトレーニングします。

**引数:**

  * `xyz`:        `XYZ` フライトデータ構造
  * `ind`:        選択されたデータインデックス
  * `meas`:       スカラー磁力計測定 [nT]
  * `itp_mapS`:   スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `x`:          `N` x `Nf` データ行列 (`Nf` は特徴の数)
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

      * `relu`  = 修正線形単位
      * `σ`     = シグモイド（ロジスティック関数）
      * `swish` = セルフゲート
      * `tanh`  = 双曲線タンジェント
      * `plot_activation()` を実行して視覚化
  * `l_window`:   （オプション）時間ウィンドウの長さ
  * `date`:       （オプション）IGRFのための測定日（小数年） [年]
  * `core`:       （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `m`:          ニューラルネットワークモデル
  * `data_norms`: データ正規化の長さ`3`のタプル `(v_scale,x_bias,x_scale)`
