```
quantile(d::dPower, q::Real)
```

`q`-Quantile of a `dPower` random variable.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
quantile(dPower, 0.95)
```

See also [`dPower`](@ref dPower).
