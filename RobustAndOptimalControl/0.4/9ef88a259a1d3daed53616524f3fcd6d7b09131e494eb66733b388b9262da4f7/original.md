```
baltrunc_unstab(sys::LTISystem; residual = false, n = missing, kwargs...)
```

Balanced truncation for unstable models. An additive decomposition of sys into `sys = sys_stable + sys_unstable` is performed after which `sys_stable` is reduced. The order `n` must not be less than the number of unstable poles.

See `baltrunc2` for other keyword arguments.
