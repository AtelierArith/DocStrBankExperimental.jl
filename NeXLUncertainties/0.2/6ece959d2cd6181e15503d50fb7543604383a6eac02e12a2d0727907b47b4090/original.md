```
add(ka::Real, a::UncertainValue, kb::Real, b::UncertainValue, cc::AbstractFloat)
```

Computes `ka*a + kb*b` where `a` and `b` are UncertainValue and `cc` is the correlation coefficient defined as `cc = covar(a,b)/( σ(a), σ(b) )`
