```
sequential_backtest_market(strategy_logic::Function, market_history::VolumeMarketHistory) -> Vector{Real}, Vector{Real}
```

戦略が資産ごとの投資金額の配列を返すためのシンプルな逐次バックテスト機能。状態を持つ戦略に最適です。

API:

```julia
wealth_strategy, returns_strategy = sequential_backtest_market(market_history; date_range=date_range) 
    do market, past_returns
    # ... 戦略の定義 ...
    return investment_decision
end
```

引数:

  * `strategy_logic::Function`: 投資戦略を表す関数。
  * `market_history::MarketHistory`: 市場の履歴。

オプションのキーワード引数:

  * `date_range`: 市場の履歴に対応するエントリを持つシミュレーションする日付。
