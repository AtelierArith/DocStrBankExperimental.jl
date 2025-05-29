```
quantilecint(pd::DependentScalingModel, data::IDFdata, d::Real, p::Real, H::PDMat{<:Real}, α::Real=.05)
```

Compute the approximate Wald quantile confidence interval of level (1-`α`) of the quantile of level `q` for the duration `d`.

## Details

This function uses the Hessian matrix `H` provided in the argument.  
