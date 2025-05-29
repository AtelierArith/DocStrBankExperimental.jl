```
backtest(vms::Vector{<:VaRModel}, data::Vector{<:Real},
              windowsize::Integer;dataset_name::String="データセット名が指定されていません",
              lags::Integer=5)
```

複数の `VaRModel` を提供されたデータセットでバックテストします。 `windowsize` は、バリュー・アット・リスクの予測に使用されるサンプル内観測の数を指定します。 `backtest(...)` は `BacktestResult` のベクターを返します。オプションのパラメータ `lags` は、時間の独立性のテストで使用されるラグの数を制御します。 `dataset_name` は `BacktestResult` に含めるために提供される場合があります。
