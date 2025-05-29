```
mean_and_std(x, [w::AbstractWeights], [dim]; corrected=false) -> (mean, std)
```

コレクション `x` の平均と標準偏差を返します。`x` が `AbstractArray` の場合、`dim` をタプルとして指定することで、これらの次元にわたる統計を計算できます。推定値に重みを付けるために、重みベクトル `w` を指定できます。最後に、`corrected=true` の場合、標準偏差の計算にバイアス補正が適用されます。詳細については [`std`](@ref) ドキュメントを参照してください。
