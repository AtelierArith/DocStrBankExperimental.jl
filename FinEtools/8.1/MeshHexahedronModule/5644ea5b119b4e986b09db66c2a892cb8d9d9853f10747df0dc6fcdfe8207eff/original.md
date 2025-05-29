```
H8hexahedron(xyz::Matrix{T}, nL::IT, nW::IT, nH::IT; blockfun = nothing) where {T<:Number, IT<:Integer}
```

Mesh of a general hexahedron given by the location of the vertices.

`xyz` = One vertex location per row; Either two rows (for a rectangular      block given by the its corners),  or eight rows (general hexahedron). `nL`,  `nW`,  `nH` = number of elements in each direction `blockfun` = Optional argument: function of the block-generating mesh function      (having the signature of the function `H8block()`).
