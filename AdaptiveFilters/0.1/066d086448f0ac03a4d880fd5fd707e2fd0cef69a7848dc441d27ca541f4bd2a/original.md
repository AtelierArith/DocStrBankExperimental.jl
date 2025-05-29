```
NLMS(n::Int, μ::T)
```

Create an `NLMS` FIR-filter with `n` coefficients (filter taps) and learning rate `0 < μ ≤ 1`. The type of `μ` determines the numeric type used by the filter.

Call the filter object like a function `ŷ, e = f(x, d)` where `x` is the input and `d` is the desired output. To create an adaptive line enhancer (ALE), set $d[k] = x[k-Δ]$ where $Δ$ is a positive integer delay, like 1.
