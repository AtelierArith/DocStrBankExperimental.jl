```
convert_arguments(P, x::RangeLike, y::RangeLike, z::AbstractMatrix)
```

Takes one or two ClosedIntervals `x` and `y` and converts them to closed ranges with size(z, 1/2).
