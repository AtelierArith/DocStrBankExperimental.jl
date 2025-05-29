```
change_bids!(market::VolumeMarket, model::JuMP.Model, decision_variables)
```

最適化モデルを解決し、`decision_variables`の最適値に新しい入札を設定します。
