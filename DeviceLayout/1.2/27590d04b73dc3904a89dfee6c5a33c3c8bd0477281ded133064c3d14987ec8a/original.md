```
mutable struct ArrayReference{S,T} <: GeometryReference{S,T}
    structure::T
    origin::Point{S}
    deltacol::Point{S}
    deltarow::Point{S}
    col::Int
    row::Int
    xrefl::Bool
    mag::Float64
    rot::Float64
end
```

Array of `structure` starting at `origin` with `row` rows and `col` columns, spanned by vectors `deltacol` and `deltarow`. Optional x-reflection `xrefl`, magnification factor `mag`, and rotation angle `rot` for the array as a whole. If an angle is given without units it is assumed to be in radians.

The type variable `T` is to avoid circular definitions.
