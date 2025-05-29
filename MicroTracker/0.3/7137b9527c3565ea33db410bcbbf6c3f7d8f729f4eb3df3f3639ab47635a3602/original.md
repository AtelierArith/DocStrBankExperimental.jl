```
estimate_omega(x::AbstractVector, y::AbstractVector)
```

Get the highest frequency peak of `x, y` data and return the corresponding `xf` divided by 2.

This works for rolling microbots when the `y` data exhibits two peaks every rotation. Depending on the data, this could be the `Angle`, `Major_m`, or `V` columns.
