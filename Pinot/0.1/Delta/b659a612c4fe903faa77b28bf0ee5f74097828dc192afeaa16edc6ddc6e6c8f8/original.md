```
transform(a::Vector{Range}, b::Vector{Range}, priority=Left) -> Vector{Range}
```

Produces a version of `b` transformed over `a` such that:

```julia
Pinot.apply(Pinot.apply(text, a), Pinot.transform(a, b, Pinot.Left)) ==
    Pinot.apply(Pinot.apply(text, b), Pinot.transform(b, a, Pinot.Right))
```

`priority` is used to indicate which change happened before in conflict resolution.
