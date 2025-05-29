```
rotation(ref::GeometryReference; α0=0)
```

The change in angle when applying `transformation(ref)` to a line originally at `α0` CCW from the `x`-axis.

Equivalent to `rotation(transformation(ref); α0=α0)`.
