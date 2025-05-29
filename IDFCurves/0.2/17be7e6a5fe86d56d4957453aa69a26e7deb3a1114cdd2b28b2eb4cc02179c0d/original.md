```
qqplotci(fm::MarginalScalingModel, α::Real=.05, H::PDMat{<:Real})
```

Quantile-Quantile plot along with the confidence/credible interval of level `1-α`.

## Details

This function uses the Hessian matrix `H` provided in the argument.  
