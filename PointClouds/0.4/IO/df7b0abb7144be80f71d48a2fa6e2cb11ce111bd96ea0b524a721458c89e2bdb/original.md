```
source_id([T], p::PointRecord)
source_id([T], points, inds = :)
```

Obtain the source ID of a point record, which is defined as an integer between 0 and 65535. This may be used to group points that were recorded in a uniform manner, e.g. during the same flight line.

See also: [`PointRecord`](@ref)
