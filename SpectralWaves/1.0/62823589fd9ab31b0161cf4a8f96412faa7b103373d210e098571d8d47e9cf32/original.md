```
water_velocity(p::Problem, x::Real, z::Real, n::Integer, c::Symbol)
```

Compute the water velocity component `u` or `w` using the symbol `:x` or `:z` at position `(x, z)`, and for time instant `n`.
