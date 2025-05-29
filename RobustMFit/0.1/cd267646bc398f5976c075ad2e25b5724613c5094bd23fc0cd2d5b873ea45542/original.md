```
findkU(d::UnivariateDistribution, spec::MSetting)
findkU(d::dPower, spec::MSetting)
updatekU(d::UnivariateDistribution, spec::MSetting)
updatekU(d::dPower, spec::MSetting)
```

Function to find the lower tuning constant in M-estimation given the lower tuning constant. Assuming the distribution of X is `d`, solves E(ψ(Z)) = 0 where $Z = (X - E(X))/std(X)$ if `d` if a univariate distribution and $Z = (X1 i - E(X^i))/std(X^i)$ if `d` if of type `dPower`.

`findkU` returns the upper tuning constant, `updatekU` returns an updated specification `spec`.

If the specification is `HampelSetting`, there is a lower tuning constant vector `kL`, not a scalar. The function then searches for `c ⋅ kL` for suitable scalar `c`.

# Example

```julia
d = Poisson(10)
spec = Huber(0.5)
findkU(d, spec)
```

See also [`dPower`](@ref dPower).
