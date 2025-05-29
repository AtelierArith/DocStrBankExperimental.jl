```
calculate_mean_abs_distance_covar(
    cov1::CovarianceMatrix,
    cov2::CovarianceMatrix,
    decimal_places::Integer = 8;
    return_nans_if_symbols_dont_match::Bool = true,
)
```

2つの `CovarianceMatrix` の共分散行列（自然時間単位で）間の平均絶対距離（要素ごとにL1ノルム）を計算します。2つの `CovarianceMatrix` の間でラベルが異なる場合は未定義です。

この関数は、実際の共分散行列間の距離を示す1つの実数を返す点で、calculate*mean*abs_distanceとは異なります。相関とボラティリティの観点から距離を示すタプルではありません。

### 入力

  * `cov1` - 最初の `CovarianceMatrix`
  * `cov2` - 2番目の `CovarianceMatrix`
  * `decimal_places` - 結果を表示する小数点以下の桁数。
  * `return_nans_if_symbols_dont_match` - シンボルが一致しない場合、エラーにすべきか。falseの場合は、両方の `CovarianceMatrix` に共通するシンボルのみを比較します。

### 戻り値

  * 実数
