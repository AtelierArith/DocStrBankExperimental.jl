```julia
plot_tearsheet(
    strategy_equity_curve::DataFrame,
    benchmark_equity_curve::DataFrame;
    title::String = "戦略とベンチマークのティアシート",
)
```

バックテスト結果をベンチマークと比較してティアシートをプロットします。

DataFrameには以下の列が必要です：

  * 
  * `total_equity`: ポートフォリオの総価値

## パラメータ

  * `strategy_equity_curve::DataFrame`
  * `benchmark_equity_curve::DataFrame`
  * `title::String`
