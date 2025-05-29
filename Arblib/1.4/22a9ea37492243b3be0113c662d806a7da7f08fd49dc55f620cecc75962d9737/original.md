```
setball(::Type{Arb}, m, r; prec = _precision(m))
```

Returns an `Arb` with the midpoint and radius set to `m` and `r` respectively.

Note that the `m` is converted to an `Arf` and therefore rounded. So for example `setball(1 // 3, 0)` will not contain $1 / 3$.

See also [`getball`](@ref) and [`add_error`](@ref).
