```
var(d::dPower)
```

Variance of a `dPower` random variable.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
var(dPower)
```

See also [`dPower`](@ref dPower).
