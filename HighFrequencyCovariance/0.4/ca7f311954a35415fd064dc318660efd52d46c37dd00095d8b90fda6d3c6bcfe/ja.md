```
relabel(covar::CovarianceMatrix, mapping::Dict{Symbol,Symbol})
```

これは、すべての資産に別の名前を付けるために、CovarianceMatrix構造体のラベルを変更します。

### 入力

  * `covar` - ラベルを変更したい`CovarianceMatrix`オブジェクト。
  * `mapping` - あなたが持っている名前から、あなたが望む名前へのマッピングを持つ辞書。

### 戻り値

  * 入力したものと同じ`CovarianceMatrix`ですが、新しいラベルが付いています。
