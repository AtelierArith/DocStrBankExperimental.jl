```
struct ToTolerance{T<:Coordinate} <: GeometryEntityStyle
    atol::T
end
```

Style for rendering an entity to absolute tolerance `atol`.

Equivalent to passing or overriding the keyword `atol` when rendering this entity.
