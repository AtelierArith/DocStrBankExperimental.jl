```
seasonality(t, x; y0 = year(t[1])) → dates, vals
```

Calculate the "seasonality" of a vector `x` defined with respect to a datetime vector `t` and return `dates, vals`. `dates` are all unique dates present in `t` *disregarding the year* (so only the month and day are compared). The `dates` have as year entry `y0`. `vals` is a vector of vectors, where `vals[i]` are all the values of `x` that have day and month same as `dates[i]`. The elements of `vals` are sorted as encountered in `x`.

Typically one is interested in `mean.(vals)`, which actually is the seasonality, and `std.(vals)` which is the interannual variability at each date.

```
seasonality(A::ClimArray) → dates, vals
```

If given a `ClimArray`, then the array must have only one dimension (time).
