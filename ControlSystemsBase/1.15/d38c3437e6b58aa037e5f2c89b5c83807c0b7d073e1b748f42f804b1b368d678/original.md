```
fig = pzmap(fig, system, args...; hz = false, kwargs...)
```

Create a pole-zero map of the `LTISystem`(s) in figure `fig`, `args` and `kwargs` will be sent to the `scatter` plot command.

To customize the unit-circle drawn for discrete systems, modify the line attributes, e.g., `linecolor=:red`.

If `hz` is true, all poles and zeros are scaled by 1/2π.
