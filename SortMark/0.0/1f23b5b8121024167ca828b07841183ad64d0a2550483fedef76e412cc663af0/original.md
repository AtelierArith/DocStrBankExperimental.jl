```
function stat!(df, a=1, b=2)
```

Compute comparative stats for the `a`th and `b`th algorithm tested in `df`.

Returns the 95% confidence interval for the ratio of runtimes a/b for each row.
