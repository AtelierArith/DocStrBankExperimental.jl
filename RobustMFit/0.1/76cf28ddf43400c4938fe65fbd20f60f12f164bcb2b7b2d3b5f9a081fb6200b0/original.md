```
nParEff(d::UnivariateDistribution)
```

Get the number of parameters of a distribution `d` to be estimated. Some parameters are treated constant.

# Example

```julia
d1 = Normal()
nParEff(d1)

d2 = Binomial(10, 0.4)
nParEff(d2)
```
