```
convert_arguments(P, x, y, z)::Tuple{ClosedInterval, ClosedInterval, Matrix}
```

Takes 2 ClosedIntervals's `x`, `y`, and an AbstractMatrix `z`, and converts the closed range to linspaces with size(z, 1/2) `P` is the plot Type (it is optional).
