```
summarize(data::AbstractArray, stats_funs...; kwargs...) -> SummaryStats
```

Compute the summary statistics in `stats_funs` on each param in `data`, with size `(draws, chains, params)`.
