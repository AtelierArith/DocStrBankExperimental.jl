```
lp(r::LocalProjectionResult{<:SmoothLP}, λ::Real; vce=nothing)
```

Reestimate the smooth local projection with the smoothing parameter `λ`. Optionally, an alternative variance-covariance estimator may be specified with the keyword `vce`.
