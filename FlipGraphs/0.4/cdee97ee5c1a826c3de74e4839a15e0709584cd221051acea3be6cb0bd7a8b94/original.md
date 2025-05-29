```
is_flippable(D::DeltaComplex, e::Integer) :: Bool
```

Return `true` if the given edge can be flipped.

This is always the case if the edge does not connect a `TriFace` to itself.
