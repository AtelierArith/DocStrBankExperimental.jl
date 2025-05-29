```julia
plot_tearsheet(
    strategy_equity_curve::DataFrame,
    benchmark_equity_curve::DataFrame;
    title::String = "Strategy vs Benchmark Tearsheet",
)
```

Plot a tearsheet of backtesting results compared to a benchmark. 

The DataFrame has to have the following columns:

  * 
  * `total_equity`: total portfolio value

## Parameters

  * `strategy_equity_curve::DataFrame`
  * `benchmark_equity_curve::DataFrame`
  * `title::String`
