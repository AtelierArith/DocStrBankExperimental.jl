```
IndicatorProcess(func, prob)
```

Indicator process with multivariate geostatistical `func`tion (e.g., multivariate covariance) and a priori `prob`abilities.

```
IndicatorProcess(transiogram, prob=proportions(transiogram))
```

Alternatively, construct indicator process from `transiogram`.

## Examples

```julia
# covariance and explicit probabilities
IndicatorProcess([1.0 0.5; 0.5 1.0] * SphericalCovariance(), [0.8, 0.2])

# transiogram and implicit probabilities
IndicatorProcess(LinearTransiogram())

# transiogram and explicit probabilities
IndicatorProcess(ExponentialTransiogram(), [0.8, 0.2])
```
