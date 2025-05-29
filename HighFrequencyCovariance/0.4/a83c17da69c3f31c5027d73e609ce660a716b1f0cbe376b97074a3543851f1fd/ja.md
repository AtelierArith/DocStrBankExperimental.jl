```
calculate_mean_abs_distance(
    cov1::CovarianceMatrix,
    cov2::CovarianceMatrix,
    decimal_places::Integer = 8;
    return_nans_if_symbols_dont_match::Bool = true,
)
```

2つの`CovarianceMatrix`間の平均絶対距離（L1ノルムにおける要素ごと）を計算します。2つの`CovarianceMatrix`間でラベルが異なる場合は未定義です。

### 入力

  * `cov1` - 最初の`CovarianceMatrix`
  * `cov2` - 2番目の`CovarianceMatrix`
  * `decimal_places` - 結果を表示する小数点以下の桁数。
  * `return_nans_if_symbols_dont_match` - シンボルが一致しない場合、エラーにするべきか。falseの場合は、両方の`CovarianceMatrix`で共通のシンボルのみを比較します。

### 戻り値

  * 最初のエントリに相関の距離、2番目にボラティリティの距離を持つ`Tuple`。

    calculate*mean*abs_distance(d1::Dict{Symbol,<:Real}, d2::Dict{Symbol,<:Real})

2つの`CovarianceMatrix`間の平均絶対距離（L1ノルムにおける要素ごと）を計算します。

### 入力

  * `d1` - 最初の`Dict`
  * `d2` - 2番目の`Dict`

### 戻り値

  * 一致する要素間の平均距離を持つスカラー。
