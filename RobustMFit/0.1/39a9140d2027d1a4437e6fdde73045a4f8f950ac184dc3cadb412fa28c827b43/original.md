```
logpdf(d::dPower, x::Real)
```

Logarithm of probability (density) function for `dPower` distribution.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
logpdf(dPower, 2)
```

See also [`dPower`](@ref dPower).
