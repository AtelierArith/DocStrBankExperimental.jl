```
market_model(market::VolumeMarket{T,N}, optimizer_factory::Function) -> JuMP.Model, Vector{VariableRef}
```

JuMPモデルを適切なPO変数と制約で作成します：     - 変数の投資ベクトル `w`（`budget = 1` の場合はポートフォリオの重み）。     - 投資された資金は予算を下回る必要があります。

モデルと意思決定変数のベクトルへの参照（長さN）を返します。

追加の引数：

  * `optimizer_factory`: 引数なしで呼び出せる関数で、空の `MathOptInterface.AbstractOptimizer` を返します。
