```
BasketPricingProblem(payoffs, market_inputs)
```

単一の市場シナリオの下で複数のペイオフの価格設定を行うためのコンテナ。

# フィールド

  * `payoffs::Vector{P}`       — 価格設定されるペイオフのコレクション。
  * `market_inputs::M`         — すべてのペイオフで共有される市場データ（利回り曲線、ボラティリティなど）。
