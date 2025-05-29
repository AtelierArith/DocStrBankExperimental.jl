```
std(d::dPower)
```

Standard deviation of a `dPower` random variable.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
std(dPower)
```

See also [`dPower`](@ref dPower).
