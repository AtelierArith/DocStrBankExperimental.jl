```
insupport(d::dPower, x::Real)
```

Check if `x` is in the support of distribution `d`, where `d` is of type `dPower`.

# Example

```julia
dX = Poisson(10)
dY = dPower(dX, 2)
insupport(dPower, 9)
```

See also [`dPower`](@ref dPower).
