# Extended help

```
difference(X::AbstractHyperrectangle, Y::AbstractHyperrectangle)
```

### Output

A `UnionSetArray` consisting of the union of hyperrectangles. Note that this union is in general not convex.

### Algorithm

This implementation uses `IntervalArithmetic.setdiff`.
