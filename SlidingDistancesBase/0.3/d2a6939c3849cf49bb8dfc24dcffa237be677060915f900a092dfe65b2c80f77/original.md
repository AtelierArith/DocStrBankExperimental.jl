```
sliding_mean_std(x::AbstractVector{T}, kb, kf)
```

Return sliding mean and variance over windows of length `kb + kf + 1`, where `kb` data points before and `kf` after the center of the window are used.

The returned arrays will have the same lengths as the input `x`.
