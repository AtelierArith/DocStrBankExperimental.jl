```
TruncBondMax{T} <: SVDTrunc
```

[`TruncBond`](@ref)と同様ですが、オブジェクトの作成以来の最大誤差 $\sqrt{\frac{\sum_{k=m'+1}^m\lambda_k^2}{\sum_{k=1}^m\lambda_k^2}}$ も保存します。

# フィールド

  * `mprime`: 保持する特異値の数
  * `maxerr`: 最大誤差を保存する1要素ベクトル
