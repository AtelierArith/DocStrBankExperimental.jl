```
DF2TFilter(coef[, si])
```

係数 `coef` を持つ状態を持つ直接形 II 転置フィルタを構築します。`si` は初期フィルタ状態を表すオプションの配列で（デフォルトはゼロ）、`f` が `PolynomialRatio`、`Biquad`、または `SecondOrderSections` の場合、フィルタリングは直接実装されます。`f` が `ZeroPoleGain` オブジェクトの場合、最初に `SecondOrderSections` オブジェクトに変換されます。
