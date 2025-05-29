```
proportions(x, levels=span(x), [wv::AbstractWeights])
```

`x`の範囲`levels`に存在する値の割合を返します。`counts(x, levels) / length(x)`と同等です。

重みのベクトル`wv`が提供される場合、原始的なカウントの割合ではなく、重みの割合が計算されます。
