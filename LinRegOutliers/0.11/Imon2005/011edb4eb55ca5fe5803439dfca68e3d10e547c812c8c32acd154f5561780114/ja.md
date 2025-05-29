```
imon2005(setting)
```

与えられた回帰設定に対して Imon 2005 アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: 回帰設定。

# 説明

このアルゴリズムは、よく知られた回帰診断 DFFITS の拡張である GDFFITS 診断を推定します。GDFFITS は複数の外れ値を検出するために使用されるのに対し、元の DFFITS は単一の外れ値を検出するために使用されました。

# 出力

  * `["crit"]`: 使用されるクリティカル値
  * `["gdffits"]`: 観測値に対して計算された GDFFITS 診断の配列
  * `["outliers"]`: 外れ値のインデックスの配列。
  * `["betas"]`: 回帰係数のベクトル。

# 注意事項

実装は、論文で提案されているように LMS ではなく LTS を使用しています。

# 参考文献

A. H. M. Rahmatullah Imon (2005) Identifying multiple influential observations in linear regression,  Journal of Applied Statistics, 32:9, 929-946, DOI: 10.1080/02664760500163599
