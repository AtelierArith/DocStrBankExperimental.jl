```
divide(n::UncertainValue, d::UncertainValue, cc::AbstractFloat)
```

Computes `n/d` where `n` and `d` are UncertainValue and `cc` is the correlation coefficient defined as `cc = covar(n,d)/( σ(n), σ(d) )`
