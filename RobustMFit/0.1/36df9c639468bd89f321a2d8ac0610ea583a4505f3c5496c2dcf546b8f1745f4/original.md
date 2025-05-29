```
skewness(d::dPower)
```

Skewness of a `dPower` random variable.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
skewness(dPower)
```

See also [`dPower`](@ref dPower).
