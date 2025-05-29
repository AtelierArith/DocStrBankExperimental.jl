```
dPower(d::UnivariateDistribution, p::Int64)
```

A data type describing the power of a univariate random variable X. Given the distribution of X: `d` and an integer `i`, the type describes $X^i$.

# Example

```julia
    dX = Poisson(10)
    dY = dPower(d, 2)
```
