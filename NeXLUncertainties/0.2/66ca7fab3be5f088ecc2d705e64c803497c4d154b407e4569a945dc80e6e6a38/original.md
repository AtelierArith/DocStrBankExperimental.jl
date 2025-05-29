```
multiply(a::UncertainValue, b::UncertainValue, cc::AbstractFloat)
```

Computes `a*b` where `a` and `b` are UncertainValue and `cc` is the correlation coefficient defined as `cc = covar(a,b)/( σ(a), σ(b) )`
