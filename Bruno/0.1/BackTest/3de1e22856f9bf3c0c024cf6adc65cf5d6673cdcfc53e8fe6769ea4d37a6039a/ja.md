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

`strategy_returns()` 関数と一緒に使用される関数です。 `strategy()` 関数は、特定の取引またはヘッジ戦略のための売買行動を定義します。 `strategy_returns()` 関数と一緒に使用するには、新しい `Hedging` サブタイプを定義してディスパッチを可能にし、この新しいタイプを `strategy_mode` 引数でディスパッチする新しい `strategy()` メソッドを書きます。 詳細についてはパッケージのドキュメントを参照してください。

## 引数

  * `fin_obj`: 戦略が定義されている FinancialInstrument
  * `pricing_model`: FinancialInstrument の価格を設定するために `price!()` 関数によって使用される価格モデル
  * `holdings`: `strategy_returns()` 関数によって提供される FinancialInstruments とベース資産の現在の保有の辞書
  * `step`: `strategy_returns` が現在実行中の `n_timesteps` のステップ番号
