```
mean_and_cov(x, [wv::AbstractWeights,] vardim=1; corrected=false) -> (mean, cov)
```

平均と共分散行列をタプルとして返します。重みベクトル `wv` を指定することができます。`vardim` は、変数が行列の列であるか (`1`) 行であるか (`2`) を指定します。最後に、`corrected=true` の場合、共分散計算にバイアス補正が適用されます。詳細については [`cov`](@ref) ドキュメントを参照してください。
