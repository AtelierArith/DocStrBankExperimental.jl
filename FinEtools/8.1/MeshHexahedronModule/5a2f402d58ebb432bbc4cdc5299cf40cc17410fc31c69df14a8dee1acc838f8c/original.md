```
H8elliphole(
    xradius::T,
    yradius::T,
    L::T,
    H::T,
    T::T,
    nL::IT,
    nH::IT,
    nW::IT,
    nT::IT,
) where {T<:Number, IT<:Integer}
```

Mesh of one quarter of a rectangular plate with an elliptical hole.

`xradius`,`yradius` = radii of the ellipse, `L`,`H` = dimensions of the plate, `Th` = thickness of the plate `nL`,`nH`= numbers of edges along the side of the plate; this is also   the number of edges along the circumference of the elliptical hole `nW` = number of edges along the remaining straight edge (from the hole   in the radial direction),
