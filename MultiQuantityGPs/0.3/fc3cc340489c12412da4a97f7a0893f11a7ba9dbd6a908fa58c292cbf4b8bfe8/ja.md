```julia
struct MQGP{T}
```

2D入力を持つ複数の量のための信念モデル構造体と関数。

マルチクォンティティガウス過程の上に設計されていますが、単一の量でも使用できます。

そのインターフェース: `X -> μ, σ` (SampleInputs -> 平均、標準偏差)
