```
WeightedMarginLoss{L,W} <: MarginLoss
```

は、ある種のバイナリ損失 `L` の再重み付けされたバージョンを表すために使用できます。重み係数 `W` は `[0, 1]` の範囲内でなければならず、正のクラスの相対的な重みを示します。一方、負のクラスの相対的な重みは `1 - W` になります。
