```
H8block(Length::T, Width::T, Height::T, nL::IT, nW::IT, nH::IT) where {T<:Number, IT<:Integer}
```

Make  a mesh  of a 3D block consisting of  eight node hexahedra.

Length, Width, Height= dimensions of the mesh in Cartesian coordinate axes, smallest coordinate in all three directions is  0 (origin) nL, nW, nH=number of elements in the three directions
