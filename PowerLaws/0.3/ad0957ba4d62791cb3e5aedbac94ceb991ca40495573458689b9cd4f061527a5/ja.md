```
DistributionComparison
```

この関数は、非入れ子分布のためのVuongテストとClarkeテストを計算します。これは、任意のデータセットにパワー法則分布を適合させることが可能であるため、必要です。この関数は、[Non nested model selection for spatial count regression models with application to health insurance](https://mediatum.ub.tum.de/doc/1083601/1083601.pdf)に従って実装されました。

# 引数

  * `d1`: 比較する最初の分布。
  * `d2`: 比較する2番目の分布。
  * `data`: 比較するデータ。
  * `sig_level`: 有意水準。デフォルトは`0.05`です。

# 戻り値

  * `DistributionComparison`: 比較に関するすべての必要な情報を含む構造体。
