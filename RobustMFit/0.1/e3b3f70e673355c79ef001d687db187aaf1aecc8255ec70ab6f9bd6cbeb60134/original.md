```
findCorr(d::UnivariateDistribution, spec::MSetting)
findCorr(d::dPower, spec::MSetting)
```

Function to find the correction term in M-estimation. Computes the expectation of ψ(Z) with Z = (X - μ)/σ, where X has distribution `d`. μ and σ are the mean and standard deviation of X. If `d` is of type `dPower` with power i, computes expectation of ψ(Z) with $Z = (X^i - μ)/σ$ where μ and σ are the expectation and standard deviation of $X^i$.

# Example

```julia
d = Poisson(10)
spec1 = Huber(1.5)
spec2 = Huber(2)
findCorr(d, spec1)
findCorr(dPower(d, 2), spec2)
```

See also [`dPower`](@ref dPower).
