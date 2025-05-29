```
quantile(fm::pwmAbstractExtremeValueModel, p::Real)::Vector{<:Real}
```

Compute the quantile of level `p` from the fitted model. For the probability weighted moment method, the model has to be stationary.
