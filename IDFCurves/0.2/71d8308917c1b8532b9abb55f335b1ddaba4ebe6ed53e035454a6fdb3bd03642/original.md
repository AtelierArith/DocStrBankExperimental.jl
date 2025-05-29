```
quantilecint(pd::DependentScalingModel, data::IDFdata, d::Real, p::Real, α::Real=.05)
```

Compute the approximate Wald quantile confidence interval of level (1-`α`) of the quantile of level `p` for the duration `d`.
