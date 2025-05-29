```
all_binning_errors(X) -> bs, stds, cum_stds
```

Returns all compatible bin sizes `bs`, the corresponding standard errors `stds`, and the cumulative standard errors `cum_stds` (reduced fluctuations).

Only bin size that lead to at least 32 bins are considered.
