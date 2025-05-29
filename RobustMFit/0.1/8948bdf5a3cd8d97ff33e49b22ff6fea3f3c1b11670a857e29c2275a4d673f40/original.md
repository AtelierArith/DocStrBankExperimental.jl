```
kurtosis(d::dPower)
```

Kurtosis of a `dPower` random variable.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
kurtosis(dPower)
```

See also [`dPower`](@ref dPower).
