```
get_quantile_scores(scores, quantiles = 0.0:0.01:1.0)
```

return the quantiles of the given N dimensional anomaly `scores` cube. `quantiles` (default: `quantiles = 0.0:0.01:1.0`) is a Float range of quantiles. Any score being greater or equal `quantiles[i]` and beeing smaller than `quantiles[i+1]` is assigned to the respective quantile `quantiles[i]`.

# Examples

```
julia> scores1 = rand(10, 2)
julia> quantile_scores1 = get_quantile_scores(scores1)
```
