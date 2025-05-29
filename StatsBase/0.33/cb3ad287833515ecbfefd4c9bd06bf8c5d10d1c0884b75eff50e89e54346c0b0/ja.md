```
proportions(x, levels=span(x), [wv::AbstractWeights])
```

範囲 `levels` に存在する `x` の値の割合を返します。これは `counts(x, levels) / length(x)` と同等です。

重みのベクトル `wv` が提供される場合、原始的なカウントの割合ではなく、重みの割合が計算されます。
