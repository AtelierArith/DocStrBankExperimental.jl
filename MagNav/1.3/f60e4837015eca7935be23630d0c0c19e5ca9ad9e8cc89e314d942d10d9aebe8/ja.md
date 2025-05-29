```
run_filt(traj::Traj, ins::INS, meas, itp_mapS, filt_type::Symbol = :ekf;
         P0             = create_P0(),
         Qd             = create_Qd(),
         R              = 1.0,
         num_part       = 1000,
         thresh         = 0.8,
         baro_tau       = 3600.0,
         acc_tau        = 3600.0,
         gyro_tau       = 3600.0,
         fogm_tau       = 600.0,
         date           = get_years(2020,185),
         core::Bool     = false,
         map_alt        = 0,
         x_nn           = nothing,
         m              = nothing,
         y_norms        = nothing,
         terms          = [:permanent,:induced,:eddy,:bias],
         flux::MagV     = MagV([0.0],[0.0],[0.0],[0.0]),
         x0_TL          = ones(eltype(P0),19),
         extract::Bool  = true,
         run_crlb::Bool = true)
```

ナビゲーションフィルタを実行し、オプションでCramér–Rao下限（CRLB）を計算します。

**引数:**

  * `traj`:      `Traj` 軌道構造体
  * `ins`:       `INS` 慣性ナビゲーションシステム構造体
  * `meas`:      スカラー磁力計測定 [nT]
  * `itp_mapS`:  スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `filt_type`: (オプション) フィルタタイプ {`:ekf`,`:mpf`}
  * `P0`:        (オプション) 初期共分散行列
  * `Qd`:        (オプション) 離散時間プロセス/システムノイズ行列
  * `R`:         (オプション) 測定（ホワイト）ノイズ分散
  * `num_part`:  (オプション) 粒子の数、`filt_type = :mpf` のみで使用
  * `thresh`:    (オプション) 再サンプリング閾値比 {0:1}、`filt_type = :mpf` のみで使用
  * `baro_tau`:  (オプション) バロメーター時定数 [s]
  * `acc_tau`:   (オプション) 加速度計時定数 [s]
  * `gyro_tau`:  (オプション) ジャイロスコープ時定数 [s]
  * `fogm_tau`:  (オプション) FOGMのキャッチオール時定数 [s]
  * `date`:      (オプション) IGRF用の測定日（小数年） [年]
  * `core`:      (オプション) trueの場合、測定にコア磁場を含める
  * `map_alt`:   (オプション) 地図の高度 [m]
  * `x_nn`:      (オプション) ニューラルネットワーク用の `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `m`:         (オプション) ニューラルネットワークモデル
  * `y_norms`:   (オプション) `y` 正規化のタプル、すなわち `(y_bias,y_scale)`
  * `terms`:     (オプション) 使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `flux`:      (オプション) `MagV` ベクトル磁力計測定構造体
  * `x0_TL`:     (オプション) 初期トレス-ローソン係数状態
  * `extract`:   (オプション) trueの場合、出力構造体を抽出
  * `run_crlb`:  (オプション) trueの場合、Cramér–Rao下限（CRLB）を計算

**戻り値:**

  * `extract = true` かつ `run_crlb = true` の場合

      * `crlb_out`: `CRLBout` Cramér–Rao下限抽出出力構造体
      * `ins_out`:  `INSout`  慣性ナビゲーションシステム抽出出力構造体
      * `filt_out`: `FILTout` フィルタ抽出出力構造体
  * `extract = true` かつ `run_crlb = false` の場合

      * `filt_out`: `FILTout` フィルタ抽出出力構造体
  * `extract = false` かつ `run_crlb = true` の場合

      * `filt_res`: `FILTres` フィルタ結果構造体
      * `crlb_P`:   Cramér–Rao下限非線形共分散行列
  * `extract = false` かつ `run_crlb = false` の場合

      * `filt_res`: `FILTres` フィルタ結果構造体
