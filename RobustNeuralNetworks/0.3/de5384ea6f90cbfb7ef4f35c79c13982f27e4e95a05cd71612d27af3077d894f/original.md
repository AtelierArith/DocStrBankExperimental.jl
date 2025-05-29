```
set_output_zero!(m::AbstractLBDNParams)
```

Set output map of an LBDN to zero.

If the resulting model is called with 

```julia
lbdn = LBDN(m)
y = lbdn(u)
```

then `y = 0` for any `u`.
