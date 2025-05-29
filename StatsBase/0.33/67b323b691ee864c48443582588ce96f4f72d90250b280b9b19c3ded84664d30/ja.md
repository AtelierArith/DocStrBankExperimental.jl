```
mean_and_var(x, [w::AbstractWeights], [dim]; corrected=false) -> (mean, var)
```

コレクション `x` の平均と分散を返します。`x` が `AbstractArray` の場合、`dim` をタプルとして指定することで、これらの次元にわたる統計を計算できます。推定値に重みを付けるために、重みベクトル `w` を指定できます。最後に、`corrected=true` の場合、分散計算にバイアス補正が適用されます。詳細については [`var`](@ref) ドキュメントを参照してください。
