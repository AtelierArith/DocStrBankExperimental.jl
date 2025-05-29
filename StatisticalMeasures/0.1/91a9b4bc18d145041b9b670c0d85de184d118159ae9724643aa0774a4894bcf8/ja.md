```
roc_curve(ŷ, y) -> false_positive_rates, true_positive_rates, thresholds
```

バイナリ分類問題の受信者動作特性（ROC）曲線をプロットするためのデータを返します。

ここで `ŷ` は、真の観測値 `y`（`CategoricalVector`）が取る2つの値に対する `UnivariateFinite` 分布のベクトル（CategoricalDistributions.jlから）です。

`k` 個のユニークな確率がある場合、対応する `k` 個の閾値と `k+1` 個の「ビン」があり、偽陽性率と真陽性率は一定です。

  * `[0.0 - thresholds[1]]`
  * `[thresholds[1] - thresholds[2]]`
  * ...
  * `[thresholds[k] - 1]`

したがって、`thresholds` の長さが `k` の場合、`true_positive_rates` と `false_positive_rates` の長さは `k+1` になります。

お気に入りのプロットバックエンドを使用して曲線をプロットするには、`plot(false_positive_rates, true_positive_rates)` のようにします。

コアアルゴリズム: [`Functions.roc_curve`](@ref)

関連情報: [`AreaUnderCurve`](@ref). 
