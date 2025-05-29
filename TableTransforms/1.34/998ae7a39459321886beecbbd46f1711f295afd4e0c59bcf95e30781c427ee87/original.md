```
Indicator(col; k=10, scale=:quantile, categ=false)
```

Transforms continuous variable into `k` indicator variables defined by half-intervals of `col` values in a given `scale`. Optionally, specify the `categ` option to return binary categorical values as opposed to raw 1s and 0s.

Given a sequence of increasing threshold values `t1 < t2 < ... < tk`, the indicator transform converts a continuous variable `Z` into a sequence of `k` variables `Z_1 = Z <= t1`, `Z_2 = Z <= t2`, ..., `Z_k = Z <= tk`.

## Scales:

  * `:quantile` - threshold values are calculated using the `quantile(Z, p)` function with a linear range of probabilities.
  * `:linear` - threshold values are calculated using a linear range.

# Examples

```julia
Indicator(1, k=3)
Indicator(:a, k=6, scale=:linear)
Indicator("a", k=9, scale=:linear, categ=true)
```
