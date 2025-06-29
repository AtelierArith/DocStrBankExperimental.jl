```
std(x::UVAL_COLLECTION_TYPES, n::Int)
```

不確実な値のコレクションの標準偏差の分布を取得します。これは、まず `n` の長さ `L` の実現を `x` から引き出すことによって行われます。ここで、 `L = length(x)` です。次に、それらの長さ `L` の実現ごとに標準偏差が計算され、標準偏差の推定値の分布が得られます。

詳細な手順：

1. まず、データセットを提供する各不確実な値から1つのランダムな数を引き出すことによって、`x` の長さ `L` の実現を引き出します。引き出しは独立しているため、データにすでに存在しない要素間の依存関係（例えば、逐次的な相関）が実現に導入されることはありません。
2. 実現の標準偏差を計算します。これは長さ `L` のベクトルです。
3. 手順を `n` 回繰り返し、`x` の `n` 個の独立した実現を引き出します。これにより、`x` の標準偏差の `n` 個の推定値が得られ、ベクトルとして返されます。
