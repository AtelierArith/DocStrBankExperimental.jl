```
pdf(d::dPower, x::Real)
```

Probability (density) function for `dPower` distribution.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
pdf(dPower, 2)
```

See also [`dPower`](@ref dPower).
