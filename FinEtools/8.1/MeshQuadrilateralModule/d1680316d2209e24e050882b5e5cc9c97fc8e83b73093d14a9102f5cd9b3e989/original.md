```
Q4elliphole(
    xradius::T,
    yradius::T,
    L::T,
    H::T,
    nL::IT,
    nH::IT,
    nW::IT,
) where {T<:Number, IT<:Integer}
```

Mesh of one quarter of a rectangular plate with an elliptical hole.

`xradius`,`yradius` = radius of the ellipse, `L,H`= and dimensions of the plate, `nL,nH`= numbers of edges along the side of the plate; this also happens     to be the number of edges along the circumference of the elliptical     hole `nW`= number of edges along the remaining straight edge (from the hole     in the direction of the length),
