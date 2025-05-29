```
cdf(d::dPower, x::Real)
```

Cumulative distribution function for `dPower` distribution.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
cdf(dPower, 2)
```

See also [`dPower`](@ref dPower).
