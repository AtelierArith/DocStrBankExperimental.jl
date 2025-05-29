```
findkL(d::UnivariateDistribution, spec::MSetting)
findkL(d::dPower, spec::MSetting)
updatekL(d::UnivariateDistribution, spec::MSetting)
updatekL(d::dPower, spec::MSetting)
```

Function to find the lower tuning constant in M-estimation given the upper tuning constant. Assuming the distribution of X is `d`, solves E(ψ(Z)) = 0 where $Z = (X - E(X))/std(X)$ if `d` if a univariate distribution and $Z = (X1 i - E(X^i))/std(X^i)$ if `d` if of type `dPower`.

`findkL` returns the lower tuning constant, `updatekL` returns an updated specification `spec`.

If the specification is `HampelSetting`, there is an upper tuning constant vector `kU`, not a scalar. The function then searches for `c ⋅ kU` for suitable scalar `c`.

# Example

```julia
d = Poisson(10)
spec = Huber(1.5)
findkL(d, spec)
```

See also [`dPower`](@ref dPower).
