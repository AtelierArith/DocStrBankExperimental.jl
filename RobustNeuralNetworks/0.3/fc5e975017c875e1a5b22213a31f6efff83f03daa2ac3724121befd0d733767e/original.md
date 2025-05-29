```
set_output_zero!(m::AbstractRENParams)
```

Set output map of a REN to zero.

If the resulting model is called with

```julia
ren = REN(m)
x1, y = ren(x, u)
```

then `y = 0` for any `x` and `u`.
