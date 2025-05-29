```
IF(d::UnivariateDistribution, spec::MSetting)
IF(d::dPower, spec::MSetting)
```

Influence function given the distribution `d` and a specification `spec`. Defined as function z -> -ψ(z)/E(ψder(Z)) where Z = (X - μ)/σ and z = (x - μ)/σ

# Example

```julia
d = Poisson(10)
spec = Huber(1.5)
IFpois = IF(d, spec)
IFpois(1)
```

See also MSetting: [`Huber`](@ref Huber), [`Tukey`](@ref Tukey), [`Andrew`](@ref Andrew) and [`Hampel`](@ref Hampel).
