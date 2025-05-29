```
StatsAPI.predict(ensemble::Bagging, X; consensus = median, kwargs...)
```

データセット `X` に対するモデルのアンサンブルの予測を返します。異なるモデルからの出力を集約するために使用される関数は `consensus` であり（デフォルトは `median`）、他のすべてのキーワード引数は `predict` に渡されます。

変動の直接的な推定を得るために、`consensus` 関数を `iqr`（四分位範囲）や任意の分散の尺度に変更することができます。
