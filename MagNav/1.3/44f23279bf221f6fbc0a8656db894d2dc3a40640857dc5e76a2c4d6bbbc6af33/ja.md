```
ekf_online_nn_setup(x, y, m, y_norms; N_sigma::Int = 1000)
```

オンライン学習によるニューラルネットワークの重みを用いた拡張カルマンフィルタ（EKF）のセットアップ。

**引数:**

  * `x`:       `N` x `Nf` データ行列（`Nf` は特徴量の数）
  * `y`:       長さ `N` のターゲットベクトル
  * `m`:       ニューラルネットワークモデル、スキップ接続では動作しません
  * `y_norms`: `y` の正規化のタプル、すなわち `(y_bias,y_scale)`
  * `N_sigma`: （オプション）`nn_sigma` を作成するために使用するニューラルネットワークの重みセットの数

**戻り値:**

  * `P0_nn`:    初期ニューラルネットワーク重みの共分散行列
  * `nn_sigma`: 初期ニューラルネットワーク重みの推定標準偏差
