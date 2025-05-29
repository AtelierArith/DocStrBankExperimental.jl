```
T4block(
    Length::T,
    Width::T,
    Height::T,
    nL::IT,
    nW::IT,
    nH::IT,
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

Generate a tetrahedral mesh  of the 3D block.

Four-node tetrahedra in a regular arrangement, with uniform spacing between the nodes, with a given orientation of the diagonals.

The mesh is produced by splitting each logical  rectangular cell into five or six tetrahedra, depending on the orientation: `orientation` = `:a`, `:b` generates 6 tetrahedra per cell. `:ca`, `:cb` generates 5 tetrahedra per cell.

Range =<0, Length> x <0, Width> x <0, Height>. Divided into elements: nL x nW x nH.
