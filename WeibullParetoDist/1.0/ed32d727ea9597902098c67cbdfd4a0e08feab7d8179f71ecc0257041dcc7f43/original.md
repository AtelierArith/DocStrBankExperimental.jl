```
truncated(d0::WeibullPareto; [lower::Real], [upper:real])
truncated(d0::WeibullPareto, lower::Real, upper::Real)
```

```julia
truncated(d0; lower=l)     # left-truncated to the interval [l, Inf)
truncated(d0; upper=u)     # right-truncated to the interval [0, u)
truncated(d0; lower=l, upper=u)     # doubly-truncated to the interval [l, u]
```
