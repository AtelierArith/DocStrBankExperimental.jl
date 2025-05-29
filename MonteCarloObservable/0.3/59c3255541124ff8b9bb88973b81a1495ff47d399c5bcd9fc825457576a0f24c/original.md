```
std_error(obs::Observable[; method=:full])
```

Estimates the standard error of the mean. Respects correlations between measurements through binning analysis.

Optional `method` keyword can be `:log`, `:full`, or `:jackknife`.

See also [`mean(obs)`](@ref).
