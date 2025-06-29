```
ekf_online_setup(flux::MagV, meas, ind = trues(length(meas));
                 Bt           = sqrt.(flux.x.^2+flux.y.^2+flux.z.^2)[ind],
                 λ            = 0.025,
                 terms        = [:permanent,:induced,:eddy,:bias],
                 pass1        = 0.1,
                 pass2        = 0.9,
                 fs           = 10.0,
                 pole::Int    = 4,
                 trim::Int    = 20,
                 N_sigma::Int = 100,
                 Bt_scale     = 50000)
```

トレス-ローソン係数のオンライン学習を伴う拡張カルマンフィルタ（EKF）のセットアップ。

**引数:**

  * `flux`:     `MagV` ベクトル磁力計測定構造体
  * `meas`:     スカラー磁力計測定 [nT]
  * `ind`:      選択されたデータインデックス
  * `Bt`:       （オプション）ベクトル磁力計測定または修正トレス-ローソンのスカラー磁力計測定の大きさ [nT]
  * `λ`:        （オプション）リッジパラメータ
  * `terms`:    （オプション）使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `pass1`:    （オプション）第一パスバンド周波数 [Hz]
  * `pass2`:    （オプション）第二パスバンド周波数 [Hz]
  * `fs`:       （オプション）サンプリング周波数 [Hz]
  * `pole`:     （オプション）バターワースフィルタの極の数
  * `trim`:     （オプション）フィルタリング後にトリムする要素の数
  * `N_sigma`:  （オプション）`TL_sigma`を作成するために使用するトレス-ローソン係数セットの数
  * `Bt_scale`: （オプション）誘導および渦電流項のスケーリングファクター [nT]

**戻り値:**

  * `x0_TL`:    初期トレス-ローソン係数状態
  * `P0_TL`:    初期トレス-ローソン共分散行列
  * `TL_sigma`: トレス-ローソン係数の推定標準偏差
