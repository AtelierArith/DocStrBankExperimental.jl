```
CovarianceMatrix(correlation::Hermitian{R},
    volatility::Vector{R},
    labels::Vector{Symbol}) where R<:Real
```

この `Struct` は三つの要素を格納します。`Hermitian` 相関行列、ボラティリティのベクトル、およびラベルのベクトルです。ラベルの順序は、ボラティリティベクトルおよび相関行列内の資産の順序と一致します。デフォルトコンストラクタが使用されます。

### 入力

  * `correlation` - `Hermitian` 相関行列。
  * `volatility` - 各資産のボラティリティ。
  * `labels` - `correlation` および `volatility` メンバーのラベル。`labels` ベクトルの n 番目のエントリには、n 番目の `volatility` メンバーにボラティリティがあり、n 番目の `correlation` メンバーの行/列に相関がある資産の名前が含まれているべきです。
  * `time_period_per_unit` - 1 単位のボラティリティに対応する期間。

### 戻り値

  * `CovarianceMatrix`。

```
