```julia
struct Pushforward{O<:InferOpt.AbstractOptimizationLayer, P} <: InferOpt.AbstractLayer
```

確率的最適化層の微分可能なプッシュフォワードで、任意の関数の後処理関数を持ちます。

`Pushforward`は、後処理がコストを返す場合に直接的な後悔最小化（経験による学習）に使用できます。

# フィールド

  * `optimization_layer::InferOpt.AbstractOptimizationLayer`: 確率的最適化層
  * `post_processing::Any`: 呼び出し可能なもの
