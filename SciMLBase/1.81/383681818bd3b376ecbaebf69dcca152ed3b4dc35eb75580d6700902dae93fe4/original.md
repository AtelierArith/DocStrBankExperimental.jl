```
DiffEqScalar(val[; update_func])
```

Represents a time-dependent scalar/scaling operator. The update function is called by `update_coefficients!` and is assumed to have the following signature:

```
update_func(oldval,u,p,t) -> newval
```
