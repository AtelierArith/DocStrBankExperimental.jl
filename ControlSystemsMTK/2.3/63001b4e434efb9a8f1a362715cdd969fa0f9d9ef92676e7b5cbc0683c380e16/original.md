```
sconnect(sys1::T, sys2::T; name)
```

Connect systems in series, equivalent to `sys2*sys1` or `series(sys1, sys2)` in ControlSystems.jl terminology
