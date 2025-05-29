```
struct Isochromat{T<:Real} <: FieldVector{3,T}
    x::T
    y::T
    z::T
end
```

Holds the x,y,z components of a spin isochromat in a FieldVector, which is a `StaticVector` (from the package `StaticArrays`) with custom fieldnames.
