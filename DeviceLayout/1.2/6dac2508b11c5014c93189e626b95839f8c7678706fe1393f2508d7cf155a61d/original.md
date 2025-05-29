```
mutable struct StructureReference{S, T} <: GeometryReference{S, T}
    structure::T
    origin::Point{S}
    xrefl::Bool
    mag::Float64
    rot::Float64
end
```

Reference to a `structure` positioned at `origin`, with optional x-reflection `xrefl`, magnification factor `mag`, and rotation angle `rot`. If an angle is given without units it is assumed to be in radians.

That is, the transformation applied by the reference is the composition of the following transformations, ordered with reflection applied first:

1. If `xrefl(f)` is `true`, a reflection across the `x`-axis
2. Rotation by `rotation(f)`
3. Magnification by `mag(f)`
4. Translation by `origin(f)`

The type variable `T` is to avoid circular definitions.
