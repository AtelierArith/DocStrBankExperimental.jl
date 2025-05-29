```
mean(d::dPower)
```

Mean/expectation of a `dPower` random variable.

# Example

```julia
dX = Normal()
dY = dPower(dX, 2)
mean(dPower)
```

See also [`dPower`](@ref dPower).
