```
IdentityRelaxation <: AbstractOptimizationLayer
```

制約が単純に忘れられるブラックボックス最適化器の単純な緩和。

適用する前に `θ` を（センタリングして）正規化することを考慮してください。

# フィールド

  * `maximizer`: 基本となる argmax 関数

参考文献: [https://arxiv.org/abs/2205.15213](https://arxiv.org/abs/2205.15213)
