```
traverse!(a::AbstractArray, c::GeometryStructure, level=1)
```

Given a coordinate system, recursively traverse its references for other coordinate systems and add to array `a` some tuples: `(level, c)`. `level` corresponds to how deep the coordinate system was found, and `c` is the found coordinate system.
