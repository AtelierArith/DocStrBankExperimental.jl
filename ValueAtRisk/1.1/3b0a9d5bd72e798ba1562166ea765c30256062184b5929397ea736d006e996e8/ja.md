```
backtest(vms::Vector{<:VaRModel}, data::Vector{<:Real},
              windowsize::Integer;dataset_name::String="データセット名が指定されていません",
              lags::Integer=5)
```

指定されたデータセットに対して単一の `VaRModel` のバックテストを行います。`windowsize` は、Value-at-Risk の予測に使用されるサンプル内観測値の数を指定します。`backtest(...)` は `BacktestResult` 型のオブジェクトを返します。オプションのパラメータ `lags` は、時間独立性のテストで使用されるラグの数を制御します。`dataset_name` は `BacktestResult` に含めるために提供される場合があります。
