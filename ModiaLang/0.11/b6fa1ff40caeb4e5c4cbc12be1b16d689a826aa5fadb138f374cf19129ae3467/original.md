```
stripUnit(v)
```

Convert the unit of `v` to the preferred units (default are the SI units), and then strip the unit. For details see `upreferred` and `preferunits` in [Unitful](https://painterqubits.github.io/Unitful.jl/stable/conversion/)

The function is defined as: `stripUnit(v) = ustrip.(upreferred.(v))`.
