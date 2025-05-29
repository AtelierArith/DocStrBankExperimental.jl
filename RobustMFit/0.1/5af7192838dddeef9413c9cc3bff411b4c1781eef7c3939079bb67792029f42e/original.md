```
rand(d::dPower)
rand(d::dPower, n::Int64)
rand(d::dPower, dims::Dims)
```

Random number generation for data type `dPower`.

# Example

```julia
dX = Poisson(10)
dY = dPower(dX, 2)
rand(dY)
rand(dY, 100)
rand(dY, (100, 100))
```

See also [`dPower`](@ref dPower).
