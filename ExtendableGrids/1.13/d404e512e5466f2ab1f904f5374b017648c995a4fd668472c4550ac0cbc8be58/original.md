```
    reference_domain(EG::Type{<:AbstractElementGeometry}, T::Type{<:Real} = Float64; scale = [1,1,1], shift = [0,0,0]) -> ExtendableGrid{T,Int32}
```

Generates an ExtendableGrid{T,Int32} for the reference domain of the specified Element Geometry. With scale and shift the coordinates can be manipulated.
