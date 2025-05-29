```
additive_gp(fs)
```

Produces the GP given by

```julia
sum(fs[1](x[1]) + fs[2](x[2]) + ... + fs[D](x[D]))
```

Requires that `length(fs)` is the same as the dimension of the inputs to be used.
