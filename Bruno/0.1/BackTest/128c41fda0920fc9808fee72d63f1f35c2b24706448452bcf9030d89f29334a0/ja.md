```
strategy(
    fin_obj::FinancialInstrument,
    pricing_model, 
    strategy_model, 
    holdings, 
    step;
    kwargs...
)
```

`strategy_returns()` 関数と一緒に使用される関数です。 `strategy()` 関数は、特定の取引またはヘッジ戦略に対する売買の振る舞いを定義します。 `strategy_returns()` 関数と一緒に使用するには、新しい `Hedging` サブタイプを定義してディスパッチを可能にし、この新しいタイプを `strategy_mode` 引数でディスパッチする新しい `strategy()` メソッドを書いてください。 詳細についてはパッケージのドキュメントを参照してください。

## 引数

  * `obj_array::Vector{<:FinancialInstrument}`: 戦略が実行される FinancialInstruments のベクター
  * `pricing_model`: `price!()` 関数が FinancialInstrument の価格を設定するために使用する価格モデル
  * `holdings`: `strategy_returns()` 関数によって提供される FinancialInstruments とベース資産の現在の保有の辞書
  * `step`: `strategy_returns` が現在実行中の `n_timesteps` のステップ番号
