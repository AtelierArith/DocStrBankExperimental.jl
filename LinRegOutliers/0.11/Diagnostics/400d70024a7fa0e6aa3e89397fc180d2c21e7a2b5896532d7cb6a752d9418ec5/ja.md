```
cooksoutliers(setting; alpha = 0.5)
```

与えられた回帰設定のクック距離を計算し、潜在的な外れ値を報告します。

# 引数

  * `setting::RegressionSetting`: 数式とデータセットを持つRegressionSettingオブジェクト。
  * `alpha::Float`: カットオフ値の確率。quantile(Fdist(p, n-p), alpha)がカットオフに使用されます。デフォルトは0.5です。

# 出力

  * `["distance"]`: クック距離。
  * `["cutoff"]`: F分布の分位点。
  * `["potentials"]`: 潜在的な回帰外れ値のインデックスのベクター。
