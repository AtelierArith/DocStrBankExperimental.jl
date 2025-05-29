```
output = sysfilter!(s::SysFilter, input)
output = sysfilter!(state, sys::StateSpace, input)
```

Returns the filtered output `y` in `y = Cx+Du, x'=Ax+Bu`

This function is used to implement control loops where a signal is filtered through a dynamical system, i.e., `U(z) = C(z)E(z)`. Initialize `state` using [`init_sysfilter`](@ref).
