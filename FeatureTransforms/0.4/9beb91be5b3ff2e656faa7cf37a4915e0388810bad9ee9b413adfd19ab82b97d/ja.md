```
LinearCombination(coefficients) <: Transform
```

いくつかの`coefficients`によって重み付けされた項のコレクションの線形結合を計算します。

N次元配列に適用されると、`LinearCombination`は指定された`dim`に沿って縮小し、(N-1)次元の配列を返します。

`inds`が指定されていない場合、変換はすべての要素に適用されます。

!!!note     現在のデフォルトは`dims=1`ですが、この動作は将来のリリースで非推奨となり、`dims`キーワード引数を明示的に指定する必要があります。     https://github.com/invenia/FeatureTransforms.jl/issues/82
