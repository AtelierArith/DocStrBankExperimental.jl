```
autolimits!()
autolimits!(la::Axis)
```

Reset manually specified limits of `la` to an automatically determined rectangle, that depends on the data limits of all plot objects in the axis, as well as the autolimit margins for x and y axis. The argument `la` defaults to `current_axis()`.
