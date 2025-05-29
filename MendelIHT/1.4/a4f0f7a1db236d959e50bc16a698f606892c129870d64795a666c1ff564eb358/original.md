```
deviance(d, y, μ, wts)
```

Calculates the sum of the squared deviance residuals (e.g. (y - μ)^2 for Gaussian case)  Each individual sqared deviance residual is evaluated using `devresid` which is implemented in GLM.jl
