```
EqualVarianceTTest(nx::Int, ny::Int, mx::Real, my::Real, vx::Real, vy::Real, μ0::Real=0)
```

Perform a two-sample t-test of the null hypothesis that samples `x` and `y` described by the number of elements `nx` and `ny`, the mean `mx` and `my`, and variance `vx` and `vy` come from distributions with equals means and variances. The alternative hypothesis is that the distributions have different means but equal variances.

Implements: [`pvalue`](@ref), [`confint`](@ref)
