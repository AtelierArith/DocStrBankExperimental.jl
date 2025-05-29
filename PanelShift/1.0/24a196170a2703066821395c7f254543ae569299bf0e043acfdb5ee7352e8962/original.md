```
panelshift!(df, id, t, x, newx, n=oneunit(df[1, t] - df[1, t]); checksorted=true)
```

Within dataframe `df`, for each group indexed by `id`, shift column `x` by `n` periods with respect to the time column `t` using `tlead`, and store the shifted column under the name `newx`. Arguments `id`, `t`, `x`, and `newx` are all column indicies in `df`.

Call `tlag` if `n` is positive and `tlead` if `n` is negative.

See also `panellead!`, `panellag!`.
