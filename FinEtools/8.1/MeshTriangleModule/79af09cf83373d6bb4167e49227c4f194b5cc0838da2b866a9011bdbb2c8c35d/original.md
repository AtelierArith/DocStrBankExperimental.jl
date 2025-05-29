```
T3circleseg(
    angle::T,
    radius::T,
    ncircumferentially::IT,
    nperradius::IT,
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

Mesh of a segment of a circle.

The subtended angle is `angle` in radians. The orientation: refer to `T3block`.
